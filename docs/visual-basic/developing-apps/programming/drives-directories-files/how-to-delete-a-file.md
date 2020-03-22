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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348789"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya Silme

Nesnenin `DeleteFile` `My.Computer.FileSystem` yöntemi bir dosyayı silmenizi sağlar. Sunduğu seçenekler arasında: silinen dosyayı Geri **Dönüşüm Kutusu'na**gönderip göndermeme, kullanıcıdan dosyanın silinmesi gerektiğini onaylamasını isteyip istememesi ve kullanıcı işlemi iptal ettiğinde ne yapması gerektiği.  
  
### <a name="to-delete-a-text-file"></a>Metin dosyasını silmek için  
  
- Dosyayı `DeleteFile` silmek için yöntemi kullanın. Aşağıdaki kod, adlı `test.txt`dosyanın nasıl silinecek olduğunu gösterir.  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Bir metin dosyasını silmek ve kullanıcıdan dosyanın silinmesi gerektiğini onaylamasını istemek için  
  
- Dosyayı `DeleteFile` silmek için yöntemi `showUI` `AllDialogs`kullanın, ayar . Aşağıdaki kod, adlandırılmış `test.txt` dosyanın nasıl silineceğini gösterir ve kullanıcının dosyanın silinmesi gerektiğini onaylamasına izin verir.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Bir metin dosyasını silmek ve Geri Dönüşüm Kutusu'na göndermek için  
  
- Parametre `DeleteFile` için belirterek `SendToRecycleBin` dosyayı silmek için yöntemi kullanın. `recycle` Aşağıdaki kod, adlı `test.txt` dosyanın nasıl silinip Geri Dönüşüm **Kutusu'na**gönderilebildiğini gösterir.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).  
  
- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).  
  
- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).  
  
- Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).  
  
- Dosya kullanımda (<xref:System.IO.IOException>).  
  
- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).  
  
- Dosya yok (<xref:System.IO.FileNotFoundException>).  
  
- Kullanıcının dosyayı silme izni yoktur veya dosya salt okunur<xref:System.UnauthorizedAccessException>( ).  
  
- Kullanıcının yeterli izine sahip olmadığı kısmi güven durumu<xref:System.Security.SecurityException>vardır ( ).  
  
- Kullanıcı işlemi iptal etti `onUserCancel` ve `ThrowException` ayarlanır<xref:System.OperationCanceledException>( ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
