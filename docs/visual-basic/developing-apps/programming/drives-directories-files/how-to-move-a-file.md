---
title: "Nasıl Yapılır: Visual Basic'te Dosya Taşıma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 95a7deeec7c5f5d997a99ba9aa4bae8d7f972b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587299"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Taşıma
`My.Computer.FileSystem.MoveFile` Yöntemi, bir dosyayı başka bir klasöre taşımak için kullanılabilir. Hedef yapı mevcut değilse oluşturulur.  
  
### <a name="to-move-a-file"></a>Bir dosyayı taşımak için  
  
-   Kullanım `MoveFile` kaynak dosyasını ve hedef dosya konumu ve dosya adını belirterek bu dosyayı taşımak için yöntem. Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2`. Kaynak dosya adı ile aynı olmasına rağmen hedef dosya adı belirtilen unutmayın.  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Dosya taşıma ve yeniden adlandırmak için  
  
-   Kullanım `MoveFile` kaynak dosya adı ve konumu, hedef konumu ve hedef konumda yeni adını belirterek bu dosyayı taşımak için yöntem. Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2` ve adlandırsa `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationFileName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).  
  
-   Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Birleşik yol noktalarını varolan bir dizin için hedef dosyanın var olduğundan ve `overwrite` ayarlanır `False`, aynı ada sahip hedef dizinde bir dosyanın kullanımda olduğunu veya kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.IO.IOException> ).  
  
-   Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   `showUI` ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`ve her iki kullanıcı işlemi iptal etti veya belirtilmemiş bir g/ç hatası oluştuğunda (<xref:System.OperationCanceledException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>  
 [Nasıl Yapılır: Dosyayı Yeniden Adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [Nasıl Yapılır: Farklı Dizinde Dosya Kopyası Oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
