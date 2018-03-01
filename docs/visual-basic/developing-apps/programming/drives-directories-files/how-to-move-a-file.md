---
title: "Nasıl Yapılır: Visual Basic'te Dosya Taşıma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96c6d1d89c0dfe4720637202b42414047e96f146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
-   `destinationFileName`olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>).  
  
-   Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Birleşik yol noktalarını varolan bir dizin için hedef dosyanın var olduğundan ve `overwrite` ayarlanır `False`, aynı ada sahip hedef dizinde bir dosyanın kullanımda olduğunu veya kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.IO.IOException> ).  
  
-   Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   `showUI`ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`ve her iki kullanıcı işlemi iptal etti veya belirtilmemiş bir g/ç hatası oluştuğunda (<xref:System.OperationCanceledException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>  
 [Nasıl yapılır: bir dosyayı yeniden adlandırın](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [Nasıl yapılır: farklı dizinde dosya kopyası oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [Nasıl yapılır: dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
