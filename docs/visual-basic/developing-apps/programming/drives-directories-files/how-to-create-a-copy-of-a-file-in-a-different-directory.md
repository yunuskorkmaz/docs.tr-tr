---
title: "Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fe37ba940172e83574505d4c82e196f60dfc1eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Farklı Dizinde Dosya Kopyası Oluşturma
`My.Computer.FileSystem.CopyFile` Yöntemi dosyaları kopyalamanızı sağlar. Parametrelerinin varolan dosyaların üzerine yazıp, dosyayı yeniden adlandırın, işlemin ilerlemesini Göster ve kullanıcı işlemi iptal etme olanağı sunar.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Bir metin dosyası başka bir klasöre kopyalamak için  
  
-   Kullanım `CopyFile` yöntemi bir kaynak dosya hem de hedef dizin belirten bir dosyasını kopyalayın. `overwrite` Parametresi varolan dosyaların üzerine gerekip gerekmediğini belirtmenizi sağlar. Aşağıdaki kod örnekleri nasıl kullanılacağını gösteren `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar, bir özel durum oluşturulmasına neden olabilir:  
  
-   Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Sistem mutlak yolu alınamadı (<xref:System.ArgumentException>).  
  
-   Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Kaynak dosyası geçerli değil veya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Birleşik yolu işaret ediyor. Varolan bir dizin (<xref:System.IO.IOException>).  
  
-   Hedef dosyanın var olduğundan ve `overwrite` ayarlanır `False` (<xref:System.IO.IOException>).  
  
-   Kullanıcının dosyaya erişmek için yeterli izinleri yok (<xref:System.IO.IOException>).  
  
-   Hedef klasörde aynı ada sahip bir dosya kullanımda (<xref:System.IO.IOException>).  
  
-   Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   `ShowUI`ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, ve kullanıcı işlemi iptal etti (<xref:System.OperationCanceledException>).  
  
-   `ShowUI`ayarlanmış `True`, `onUserCancel` ayarlanır `ThrowException`, belirtilmeyen bir g/ç hatası nedeniyle oluşur (<xref:System.OperationCanceledException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Kullanıcı gerekli izne sahip değil (<xref:System.UnauthorizedAccessException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [Nasıl yapılır: belirli düzendeki dosyaları dizine kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [Nasıl yapılır: aynı dizinde dosya kopyası oluşturma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [Nasıl yapılır: bir dizini diğerine kopyalama](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [Nasıl yapılır: bir dosyayı yeniden adlandırın](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
