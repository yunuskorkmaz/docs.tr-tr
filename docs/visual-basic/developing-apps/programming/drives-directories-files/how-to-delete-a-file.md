---
title: 'Nasıl Yapılır: Dosya Silme'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348789"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Silme

`My.Computer.FileSystem` nesnesinin `DeleteFile` yöntemi bir dosyayı silmenizi sağlar. Bunun sunduğu seçenekler arasında: Silinen dosyanın **geri dönüşüm kutusu**'na gönderilmesi, kullanıcıdan dosyanın silinip silinmeyeceğini ve Kullanıcı işlemi iptal ettiğinde ne yapılacağını onaylamasını isteyip istemediğini sorar.  
  
### <a name="to-delete-a-text-file"></a>Bir metin dosyasını silmek için  
  
- Dosyayı silmek için `DeleteFile` yöntemini kullanın. Aşağıdaki kod, `test.txt`adlı dosyanın nasıl silineceğini gösterir.  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Bir metin dosyasını silmek ve kullanıcıdan dosyanın silinmesi gerektiğini doğrulamasını istemek için  
  
- Dosyayı silmek için `DeleteFile` yöntemi kullanın, `showUI` `AllDialogs`olarak ayarlar. Aşağıdaki kod, `test.txt` adlı dosyanın nasıl silineceğini ve kullanıcının dosyanın silinmesi gerektiğini onaylamasını sağlar.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Bir metin dosyasını silmek ve geri dönüşüm kutusu 'na göndermek için  
  
- `recycle` parametresi için `SendToRecycleBin` belirterek dosyayı silmek için `DeleteFile` yöntemi kullanın. Aşağıdaki kod, `test.txt` adlı dosyanın nasıl silineceğini ve **geri dönüşüm kutusu**'na nasıl gönderileceğini gösterir.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.  
  
- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).  
  
- Dosya kullanımda (<xref:System.IO.IOException>).  
  
- Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).  
  
- Dosya yok (<xref:System.IO.FileNotFoundException>).  
  
- Kullanıcının dosyayı silme izni yok veya dosya salt okunurdur (<xref:System.UnauthorizedAccessException>).  
  
- Kullanıcının yeterli izinlere sahip olmadığı bir kısmi güven durumu (<xref:System.Security.SecurityException>) vardır.  
  
- Kullanıcı işlemi iptal etti ve `onUserCancel` `ThrowException` (<xref:System.OperationCanceledException>) olarak ayarlandı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
