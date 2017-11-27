---
title: "Nasıl Yapılır: Visual Basic'te Birden Çok Biçimli Metin Dosyalarını Okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 12362f932561bf16412e5beb364f785778c58814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Birden Çok Biçimli Metin Dosyalarını Okuma
<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesne kolay ve verimli günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar. Kullanarak bir dosyayı birden çok biçimli işleyebilir `PeekChars` dosyası aracılığıyla ayrıştırma gibi her bir satır biçimi belirlemek amacıyla yöntemi.  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Birden çok biçimli metin dosyası ayrıştırılamadı  
  
1.  Projeniz testdosyası.txt adlı bir metin dosyası ekleyin. Aşağıdaki içeriği metin dosyasına ekleyin.  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  Beklenen biçimle ve bir hata bildirildiğinde kullanılan biçimini tanımlayın. Her dizi son girişi -1, bu nedenle son alan değişken genişliğini olduğu varsayılır. Bu durum, son giriş dizideki veya 0 değerine eşit küçük oluşur.  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  Yeni bir <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> nesnesi, genişlik ve biçim tanımlama.  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  Okuma önce biçimi için test etme satırları, döngü.  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  Konsola yazma hatası.  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a>Örnek  
 Dosyadan okur tam bir örnek verilmiştir `testfile.txt`.  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi satırı belirtir özel duruma neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırında bulunan metin atanır.  
  
-   Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok. (<xref:System.Security.SecurityException>).  
  
-   Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 [Nasıl yapılır: virgülle ayrılmış metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Nasıl yapılır: Sabit genişlikli metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [TextFieldParser nesnesiyle metin dosyalarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
