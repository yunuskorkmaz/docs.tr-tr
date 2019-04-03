---
title: "Nasıl yapılır: Visual Basic'te dosya silme"
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 288c54fa854d753e9b8030463968137b32353b4e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828569"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dosya silme
`DeleteFile` Yöntemi `My.Computer.FileSystem` nesnesinin bir dosyayı silmek sağlar. Sunduğu seçenekler arasında: silinen dosyanın gönderilip gönderilmeyeceğini **geri dönüşüm kutusu**dosyasının silinip silinmediğini doğrulamak için kullanıcıya sor verilip verilmeyeceğini ve kullanıcı işlemi iptal ne yapılacağını.  
  
### <a name="to-delete-a-text-file"></a>Bir metin dosyası silinemedi  
  
-   Kullanım `DeleteFile` dosyayı silmek için yöntemi. Aşağıdaki kodu adlı dosyayı nasıl silineceği `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Bir metin dosyası silip dosyasının silinip silinmediğini doğrulamak için kullanıcıya sor  
  
-   Kullanım `DeleteFile` ayarlama, dosyayı silmek için yöntemi `showUI` için `AllDialogs`. Aşağıdaki kodu adlı dosyayı nasıl silineceği `test.txt` ve dosya silinip silinmediğini doğrulayın izin verin.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Bir metin dosyasını silin ve Geri Dönüşüm Kutusu'na göndermek için  
  
-   Kullanım `DeleteFile` dosyayı silmek için yöntemi belirtme `SendToRecycleBin` için `recycle` parametresi. Aşağıdaki kodu adlı dosyayı nasıl silineceği `test.txt` ve göndermeden **Geri Dönüşüm Kutusu'nu**.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).  
  
-   Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).  
  
-   Dosyanın kullanımda olup (<xref:System.IO.IOException>).  
  
-   Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
-   Dosya yok (<xref:System.IO.FileNotFoundException>).  
  
-   Kullanıcının dosyayı silme izni yok veya dosya salt okunur (<xref:System.UnauthorizedAccessException>).  
  
-   Hangi kullanıcı olmayan yeterli izinlere sahip bir kısmi güven durum var (<xref:System.Security.SecurityException>).  
  
-   Kullanıcı işlemi iptal edildi ve `onUserCancel` ayarlanır `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
