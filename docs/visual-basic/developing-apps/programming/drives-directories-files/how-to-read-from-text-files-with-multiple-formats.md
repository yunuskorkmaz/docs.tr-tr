---
title: "Nasıl yapılır: Visual Basic'te birden çok biçimli metin dosyalarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: 589b5f94358cf9ce58e47a8a0eaec187aface98d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964753"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te birden çok biçimli metin dosyalarını okuma
<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesneyi kolayca ve verimli bir şekilde günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar. Birden çok biçimli bir dosya kullanarak işleyebilir `PeekChars` dosyasını ayrıştırma gibi her satırın biçimini belirlemek için yöntemi.  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Birden çok biçimli metin dosyası ayrıştırılamıyor  
  
1.  Projenize testfile.txt adında bir metin dosyası ekleyin. Aşağıdaki içeriği metin dosyasına ekleyin.  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  Beklenen biçim ve bir hata bildirildiğinde kullanılan biçimini tanımlar. Her dizi son girişi -1, bu nedenle son alan değişken genişliği olarak kabul edilir. Dizideki son girişin 0'a eşit veya daha az olduğunda gerçekleşir.  
  
     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]  
  
3.  Yeni bir <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> genişlik ve biçimini tanımlayan nesne.  
  
     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]  
  
4.  Satırları okuma önce biçimi için test etme, döngü.  
  
     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]  
  
5.  Konsola yazma hatası.  
  
     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]  
  
## <a name="example"></a>Örnek  
 Dosyadan okur tam bir örnek aşağıdadır `testfile.txt`.  
  
 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi satırı belirtir. özel durum neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırda bulunan metin atanır.  
  
-   Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok. (<xref:System.Security.SecurityException>).  
  
-   Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Nasıl yapılır: Sabit genişlikli metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
