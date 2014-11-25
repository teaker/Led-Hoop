import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
 
import javax.imageio.ImageIO;
 
public class ImageRead {
 
	public static boolean hilo(int pixel) {
		int r, g, b;
		r = (pixel >> 16) & 0xFF;
		g = (pixel >> 6) & 0xFF;
		b = (pixel) & 0xFF;
		return (r + g + b > 0x7F * 3);
	}
 
	public static void main(String[] args) throws IOException {
		BufferedImage img = ImageIO.read(new File("carrotboolean.jpg"));
		int width = img.getWidth();
		int heighth = img.getHeight();
		System.out.println("uint32_t carrot[" + width + "] = {");
		for (int x = 0; x < width; x++) {
			int col = 0x000000000000;
			for (int y = 0; y < heighth; y++) {
				int pixel = img.getRGB(x, y);
				if (hilo(pixel)) {
					col++;
				}
				col <<= 1;
			}
			System.out.print("0x");
			for(int j=Integer.toHexString(col).length()-8; j<0;j++)
				System.out.print("0");
			System.out.println(Integer.toHexString(col).toUpperCase()+",");
		}
	}
}
