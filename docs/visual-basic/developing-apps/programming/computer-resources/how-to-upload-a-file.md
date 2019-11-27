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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345555"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme

<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> yöntemi bir dosyayı karşıya yüklemek ve uzak bir konuma depolamak için kullanılabilir. `ShowUI` parametresi `True`olarak ayarlanırsa, karşıya yüklemenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal etmesine izin verir.  
  
### <a name="to-upload-a-file"></a>Bir dosyayı karşıya yüklemek için  
  
- Kaynak dosyanın konumunu ve hedef dizin konumunu bir dize veya URI (Tekdüzen Kaynak tanımlayıcısı) olarak belirterek bir dosyayı karşıya yüklemek için `UploadFile` yöntemini kullanın. Bu örnek, `http://www.cohowinery.com/uploads.aspx``Order.txt` dosyayı karşıya yükler.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Bir dosyayı karşıya yüklemek ve işlemin ilerlemesini göstermek için  
  
- Kaynak dosyanın konumunu ve hedef dizin konumunu dize veya URI olarak belirterek bir dosyayı karşıya yüklemek için `UploadFile` yöntemini kullanın. Bu örnek, bir Kullanıcı adı veya parola sağlamadan dosya `Order.txt` `http://www.cohowinery.com/uploads.aspx` yükler, karşıya yüklemenin ilerlemesini gösterir ve 500 milisaniyelik zaman aşımı aralığına sahiptir.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Bir dosyayı karşıya yüklemek için Kullanıcı adı ve parola sağlama  
  
- Kaynak dosyanın konumunu ve hedef dizin konumunu bir dize veya URI olarak belirterek ve Kullanıcı adını ve parolayı belirterek bir dosyayı karşıya yüklemek için `UploadFile` yöntemini kullanın. Bu örnek, Kullanıcı adı `anonymous` ve boş bir parola sunarak dosya `Order.txt` `http://www.cohowinery.com/uploads.aspx`karşıya yükler.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durum oluşturabilir:  
  
- Yerel dosya yolu geçerli değil (<xref:System.ArgumentException>).  
  
- Kimlik doğrulama başarısız oldu (<xref:System.Security.SecurityException>).  
  
- Bağlantı zaman aşımına uğradı (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Nasıl Yapılır: Dosya İndirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
