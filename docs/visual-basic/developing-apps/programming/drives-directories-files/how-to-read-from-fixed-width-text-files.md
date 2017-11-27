---
title: "Nasıl yapılır: Visual Basic'te sabit genişlikli metin dosyalarını okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5caa124af1bf4681a4c061f453ce5e09ec2dae7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te sabit genişlikli metin dosyalarını okuma
`TextFieldParser` Nesne kolay ve verimli günlükleri gibi yapılandırılmış metin dosyalarını ayrıştırmak için bir yol sağlar.  
  
 `TextFieldType` Özelliği ayrıştırılmış dosyanın sınırlandırılmış bir dosyanın veya bir sabit genişlikli metin alanlarının sahip olup olmadığını tanımlar. Bir sabit genişlikli metin dosyasında sonunda alanının bir değişken genişliği olabilir. Alanın sonunda bir değişken genişliği olduğunu belirtmek için bir genişliğine daha az veya bu değere eşit sıfır değerine sahip olacak şekilde tanımlayın.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Sabit genişlikte metin dosyası ayrıştırılamadı  
  
1.  Yeni bir `TextFieldParser`. Aşağıdaki kod oluşturur `TextFieldParser` adlı `Reader` ve dosyayı açar `test.log`.  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  Tanımlamak `TextFieldType` özelliği olarak `FixedWidth`, genişlik tanımlama ve biçimlendirin. Aşağıdaki kod, metin sütunları tanımlar; ilk 5 karakter geniş, ikinci 10, üçüncü 11 ve dördüncü değişken genişliği.  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  Dosyadaki alanların döngü. Tüm satırları bozulmuşsa, hata raporlama ve ayrıştırma devam edin.  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  Kapat `While` ve `Using` ile engeller `End While` ve `End Using`.  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a>Örnek  
 Bu örnek dosyadan okur `test.log`.  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Belirtilen biçimi kullanarak bir satır ayrıştırılamıyor (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Özel durum iletisi satırı belirtir özel duruma neden, while <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özelliği satırında bulunan metin atanır.  
  
-   Belirtilen dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Bir kısmi güven durum kullanıcının dosyaya erişmek için yeterli izinleri yok. (<xref:System.Security.SecurityException>).  
  
-   Yol çok uzun (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [Nasıl yapılır: virgülle ayrılmış metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Nasıl yapılır: birden çok biçimli metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [TextFieldParser nesnesiyle metin dosyalarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [Sorun giderme: Okuma ve dosyalara metin yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 
