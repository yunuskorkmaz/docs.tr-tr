---
title: "Nasıl yapılır: Visual Basic'te sabit genişlikli metin dosyalarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 1df1c84e6eaf90b737b51e5512638e4a15de6866
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623447"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te sabit genişlikli metin dosyalarını okuma
`TextFieldParser` Nesneyi kolayca ve verimli bir şekilde günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.  
  
 `TextFieldType` Özelliği ayrıştırılmış dosya sınırlandırılmış bir dosyanın veya bir sabit genişlikli metin alanlarının sahip olup olmadığını tanımlar. Bir sabit genişlikli metin dosyasında, alanın sonunda bir değişken genişliği olabilir. Alanın sonunda bir değişken genişliği olduğunu belirtmek için bir genişlik daha az veya eşit sıfır olması tanımlayın.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Sabit genişlikte metin dosyası ayrıştırılamıyor  
  
1. Yeni bir `TextFieldParser`. Aşağıdaki kod oluşturur `TextFieldParser` adlı `Reader` ve dosyayı açar `test.log`.  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Tanımlama `TextFieldType` özelliği olarak `FixedWidth`, genişliği tanımlama ve biçimlendirin. Aşağıdaki kod, metin sütunlarını tanımlar; ilk 5 karakterini geniş, ikinci 10, üçüncü 11 ve dördüncü değişken genişliği.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Dosya alanları döngü. Satırları bozuk, bir hata rapor ve ayrıştırma devam edin.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Kapat `While` ve `Using` ile engeller `End While` ve `End Using`.  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte dosyadan okur `test.log`.  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi satırı belirtir. özel durum neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırda bulunan metin atanır.  
  
- Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
- Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok. (<xref:System.Security.SecurityException>).  
  
- Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
- Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Sorun giderme: Okuma ve dosyalara metin yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
