---
title: "Nasıl Yapılır: Visual Basic'te Dosya Silme"
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 2918b756d5f37de2489042a9eabfe7312841af81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588629"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Silme
`DeleteFile` Yöntemi `My.Computer.FileSystem` nesne bir dosyayı silmek sağlar. Sunduğu seçenekler arasında: silinen dosyanın gönderilip gönderilmeyeceğini **geri dönüşüm kutusu**, dosyanın silinip silinmediğini doğrulamak için kullanıcıya sor verilip ve kullanıcı işlemi iptal ettiğinde yapmanız gerekenler.  
  
### <a name="to-delete-a-text-file"></a>Bir metin dosyasını silmek için  
  
-   Kullanım `DeleteFile` dosyayı silmek için yöntem. Aşağıdaki kodda adlı dosyayı silmek gösterilmiştir `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Bir metin dosyası silip dosya silinmiş olduğunu onaylamak için kullanıcıya sor  
  
-   Kullanım `DeleteFile` dosyası ayarı silmek için yöntemi `showUI` için `AllDialogs`. Aşağıdaki kodda adlı dosyayı silmek gösterilmiştir `test.txt` ve dosyanın silinip silinmediğini doğrulamak kullanıcı izin verin.  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Bir metin dosyasını silin ve Geri Dönüşüm Kutusu'na göndermek için  
  
-   Kullanım `DeleteFile` dosyayı silmek için yöntemi belirtme `SendToRecycleBin` için `recycle` parametresi. Aşağıdaki kodda adlı dosyayı silmek gösterilmiştir `test.txt` ve göndermeden **geri dönüşüm kutusu**.  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).  
  
-   Dosyanın kullanımda olup (<xref:System.IO.IOException>).  
  
-   Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Kullanıcının dosyayı silme izni yok ya da dosyanın salt okunurdur (<xref:System.UnauthorizedAccessException>).  
  
-   Kısmi güven durum, kullanıcının yeterli izinleri yok var (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı işlemi iptal edildi ve `onUserCancel` ayarlanır `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.UIOption>  
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>  
 [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
