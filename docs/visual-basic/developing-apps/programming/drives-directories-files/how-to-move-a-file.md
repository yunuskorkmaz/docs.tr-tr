---
title: "Nasıl yapılır: Visual Basic'te dosya taşıma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 6888531918dd932ba5acb3ec967303568606d5df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722027"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dosya taşıma
`My.Computer.FileSystem.MoveFile` Yöntemi, bir dosyayı başka bir klasöre taşımak için kullanılabilir. Hedef yapı mevcut değilse oluşturulur.  
  
### <a name="to-move-a-file"></a>Bir dosyayı taşımak için  
  
-   Kullanım `MoveFile` yöntemi hem kaynak dosya hem de hedef dosya için konum ve dosya adı belirterek bu dosyayı taşır. Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2`. Kaynak dosya adı ile aynı olmasına rağmen hedef dosya adı belirtilir.  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Dosya taşıma ve yeniden adlandırmak için  
  
-   Kullanım `MoveFile` yöntemi kaynak dosya adı ve konumu, hedef konum ve hedef konumda yeni bir ad belirterek bu dosyayı taşır. Bu örnek adlı dosyayı taşır `test.txt` gelen `TestDir1` için `TestDir2` ve yeniden adlandırsa `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationFileName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).  
  
-   Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Varolan bir dizin için birleştirilmiş yolun noktaları, hedef dosya var ve `overwrite` ayarlanır `False`, hedef dizinde aynı ada sahip bir dosya veya kullanıcının dosyaya erişmek için yeterli izinlere sahip değil (<xref:System.IO.IOException> ).  
  
-   Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   `showUI` ayarlanır `True`, `onUserCancel` ayarlanır `ThrowException`ve her iki kullanıcı işlemi iptal etti veya belirtilmeyen bir g/ç hatası oluşuyor (<xref:System.OperationCanceledException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Nasıl yapılır: Dosyayı yeniden adlandırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Nasıl yapılır: Farklı dizinde dosya kopyası oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Nasıl yapılır: Dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
