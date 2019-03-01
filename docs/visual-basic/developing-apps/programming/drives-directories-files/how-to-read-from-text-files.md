---
title: "Nasıl yapılır: Visual Basic'te metin dosyalarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 45c96973f8092f8ac1f1588f70e1f4b9e1049af7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979053"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te metin dosyalarını okuma
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Yöntemi `My.Computer.FileSystem` nesnesi bir metin dosyasından okuma izin verir. Dosyanın içeriği ASCII veya UTF-8 gibi bir kodlama kullanıyorsa dosya kodlaması belirtilebilir.  
  
 Genişletilmiş karakterler içeren bir dosyadan okuma yapıyorsanız, dosya kodlamasını belirtmeniz gerekir.  
  
> [!NOTE]
>  Bir dosyayı aynı anda tek satırlık metin okumak için kullanın <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> yöntemi `My.Computer.FileSystem` nesne. `OpenTextFileReader` Yöntemi döndürür bir <xref:System.IO.StreamReader> nesne. Kullanabileceğiniz <xref:System.IO.StreamReader.ReadLine%2A> yöntemi `StreamReader` aynı anda bir dosya bir satırı okumak için nesne. Son dosya kullanarak test edebilirsiniz <xref:System.IO.StreamReader.EndOfStream%2A> yöntemi `StreamReader` nesne.  
  
### <a name="to-read-from-a-text-file"></a>Bir metin dosyasından okumak için  
  
-   Kullanım `ReadAllText` yöntemi `My.Computer.FileSystem` bir metin dosyasının içeriğini okuyup bir dize haline yolunu sağlamak için nesne. Aşağıdaki örnek, test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.  
  
     [!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>Kodlanmış bir metin dosyasından okumak için  
  
-   Kullanım `ReadAllText` yöntemi `My.Computer.FileSystem` bir metin dosyasının içeriğini okuyup bir dize haline yol ve dosya kodlama türü için nesne. Aşağıdaki örnek, UTF32 biçimindeki test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.  
  
     [!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Dizeyi arabelleğe yazmak için yeterli bellek yok (<xref:System.OutOfMemoryException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.  
  
 Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Nasıl yapılır: Sabit genişlikli metin dosyalarından okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Nasıl yapılır: Birden çok biçimli metin dosyalarını okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Sorun giderme: Okuma ve dosyalara metin yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Dosya Kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
