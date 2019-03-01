---
title: "Nasıl yapılır: Visual Basic'te virgülle ayrılmış metin dosyalarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9035bf2639033915c686d336d7d4805a7205f0ae
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968027"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te virgülle ayrılmış metin dosyalarını okuma
`TextFieldParser` Nesneyi kolayca ve verimli bir şekilde günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar. `TextFieldType` Özelliği sınırlandırılmış bir dosyanın veya bir sabit genişlikli metin alanlarının olup olmadığını tanımlar.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Sınırlandırılmış bir metin dosyasını virgül ayrıştırılamıyor  
  
1.  Yeni bir `TextFieldParser`. Aşağıdaki kod oluşturur `TextFieldParser` adlı `MyReader` ve dosyayı açar `test.txt`.  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2.  Tanımlama `TextField` türü ve ayırıcı. Aşağıdaki kod tanımlar `TextFieldType` özelliği olarak `Delimited` ve ayırıcı olarak ",".  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3.  Dosya alanları döngü. Tüm satırları bozuk, bir hata rapor ve ayrıştırma devam edin. Aşağıdaki kod, her bir alan sırayla görüntüleme ve hatalı biçimlendirilmiş herhangi bir alan raporlama dosya döngüde kalır.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4.  Kapat `While` ve `Using` ile engeller `End While` ve `End Using`.  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte dosyadan okur `test.txt`.  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi satırı belirtir. özel durum neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırda bulunan metin atanır.  
  
-   Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok. (<xref:System.Security.SecurityException>).  
  
-   Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Nasıl yapılır: Sabit genişlikli metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Sorun giderme: Okuma ve dosyalara metin yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
