---
title: 'Nasıl yapılır: Dosya Silme'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 0c8213786b8073d784f1f3ea51417741d5ad4cba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401660"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Silme

`DeleteFile` `My.Computer.FileSystem` Nesnesinin yöntemi bir dosyayı silmenizi sağlar. Bunun sunduğu seçenekler arasında: Silinen dosyanın **geri dönüşüm kutusu**'na gönderilmesi, kullanıcıdan dosyanın silinip silinmeyeceğini ve Kullanıcı işlemi iptal ettiğinde ne yapılacağını onaylamasını isteyip istemediğini sorar.  
  
### <a name="to-delete-a-text-file"></a>Bir metin dosyasını silmek için  
  
- `DeleteFile`Dosyayı silmek için yöntemini kullanın. Aşağıdaki kod, adlı dosyanın nasıl silineceğini gösterir `test.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Bir metin dosyasını silmek ve kullanıcıdan dosyanın silinmesi gerektiğini doğrulamasını istemek için  
  
- `DeleteFile`' İ ' olarak ayarlayarak dosyayı silmek için yöntemini `showUI` kullanın `AllDialogs` . Aşağıdaki kod, adlı dosyanın nasıl silineceğini `test.txt` ve kullanıcının dosyanın silinmesi gerektiğini onaylamasını sağlar.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Bir metin dosyasını silmek ve geri dönüşüm kutusu 'na göndermek için  
  
- `DeleteFile`Parametresi için belirterek dosyayı silmek için yöntemini kullanın `SendToRecycleBin` `recycle` . Aşağıdaki kod, adlı dosyanın nasıl silineceğini `test.txt` ve **geri dönüşüm**kutusu 'na nasıl gönderileceğini gösterir.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- Dosya kullanımda ( <xref:System.IO.IOException> ).  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .  
  
- Dosya yok ( <xref:System.IO.FileNotFoundException> ).  
  
- Kullanıcının dosyayı silme izni yok veya dosya salt okunurdur ( <xref:System.UnauthorizedAccessException> ).  
  
- Kullanıcının yeterli izinlere () sahip olmadığı kısmi güven durumu vardır <xref:System.Security.SecurityException> .  
  
- Kullanıcı işlemi iptal etti ve `onUserCancel` () olarak ayarlandı `ThrowException` <xref:System.OperationCanceledException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma](how-to-get-the-collection-of-files-in-a-directory.md)
