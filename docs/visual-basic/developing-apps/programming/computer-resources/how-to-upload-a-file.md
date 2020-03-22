---
title: 'Nasıl Yapılır: Karşıya Dosya Yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345555"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme

Yöntem, <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> bir dosyayı yüklemek ve uzak bir konuma depolamak için kullanılabilir. `ShowUI` Parametre `True`ayarlanmışsa, yüklemenin ilerlemesini gösteren ve kullanıcıların işlemi iptal etmesine izin veren bir iletişim kutusu görüntülenir.  
  
### <a name="to-upload-a-file"></a>Dosya yüklemek için  
  
- Kaynak `UploadFile` dosyanın konumunu ve hedef dizin konumunu dize veya URI (Tekdüzen Kaynak Tanımlayıcı) olarak belirterek dosya yüklemek için yöntemi kullanın. Bu örnek, `Order.txt` dosyayı `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Bir dosya yüklemek ve işlemin ilerlemesini göstermek için  
  
- Kaynak `UploadFile` dosyanın konumunu ve hedef dizin konumunu dize veya URI olarak belirterek dosya yüklemek için yöntemi kullanın. Bu örnek, bir `Order.txt` `http://www.cohowinery.com/uploads.aspx` kullanıcı adı veya parola sağlamadan dosyayı yükler, yüklemenin ilerlemesini gösterir ve 500 milisaniyelik bir zaman aralığına sahiptir.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Bir dosya yüklemek için, kullanıcı adı ve parola sağlama  
  
- Bir `UploadFile` dosyayı yüklemek, kaynak dosyanın konumunu ve hedef dizin konumunu dize veya URI olarak belirterek ve kullanıcı adını ve parolayı belirtmek için yöntemi kullanın. Bu örnek, `Order.txt` dosyayı `http://www.cohowinery.com/uploads.aspx`kullanıcı adı `anonymous` ve boş bir parola sağlayan dosyaya yükler.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durum atabilir:  
  
- Yerel dosya yolu geçerli<xref:System.ArgumentException>değil ( ).  
  
- Kimlik doğrulama<xref:System.Security.SecurityException>başarısız oldu ( ).  
  
- Bağlantı zamanlanmış (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Nasıl Yapılır: Dosya İndirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
