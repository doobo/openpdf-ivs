# openpdf-ivs

## 如何添加,注意先后顺序,ivs要在前面,因为是替换openPdf里面的类
```
<dependency>
    <groupId>com.github.doobo</groupId>
    <artifactId>openpdf-ivs</artifactId>
    <version>1.0</version>
</dependency>
 
<dependency>
    <groupId>com.github.librepdf</groupId>
    <artifactId>openpdf</artifactId>
    <version>1.3.20</version>
</dependency>
```

## 简单使用
```java
import com.lowagie.text.*;
import com.lowagie.text.pdf.PdfWriter;
import org.junit.jupiter.api.Test;

import java.io.FileOutputStream;
import java.io.IOException;

public class IvsFontsTests {

	@Test
	void testCommon() {
		FontFactory.register("pdf/Ming_MSCS_Full.ttf");
		Document document = new Document();
		try {
			PdfWriter.getInstance(document,
				new FileOutputStream("target/HelloWorld.pdf"));
			document.open();
			Font font =  FontFactory.getFont("Ming_MSCS_Full", "Identity-H",true,20,Font.BOLD,null);
			Paragraph paragraph = new Paragraph(25,
				new Chunk("拐拐\uDB40\uDD06\uDB40\uDD01,\uD846\uDE74\uD846\uDE74\uDB40\uDD01,\uD843\uDC98\uD843\uDC98\uDB40\uDD01,黙黙\uDB40\uDD02,髥髥\uDB40\uDD02,\uD85C\uDCF0\uD85C\uDCF0,飬飬\uDB40\uDD01,隶隶\uDB40\uDD04,鏆鏆\uDB40\uDD02\uDB40\uDD09,衆衆\uDB40\uDD08,录录\uDB40\uDD03,廸廸\uDB40\uDD04,啫啫\uDB40\uDD01,啚啚\uDB40\uDD05,啗啗\uDB40\uDD02,㛇㛇\uDB40\uDD02"
					,font)
			);
			paragraph.setFont(font);
			document.add(paragraph);
			document.close();
		} catch (DocumentException de) {
			System.err.println(de.getMessage());
		} catch (IOException ioe) {
			System.err.println(ioe.getMessage());
		}
	}
}
```
