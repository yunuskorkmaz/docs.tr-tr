---
title: 'Nasıl yapılır: Karşıya Dosya Yükleme'
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

<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Yöntemi bir dosyayı karşıya yüklemek ve uzak bir konuma depolamak için kullanılabilir. `ShowUI` Parametresi olarak `True`ayarlanırsa, karşıya yüklemenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal etmesine izin verir.  
  
### <a name="to-upload-a-file"></a>Bir dosyayı karşıya yüklemek için  
  
- Kaynak dosyanın `UploadFile` konumunu ve hedef dizin konumunu DIZE veya URI (Tekdüzen Kaynak tanımlayıcısı) olarak belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın. Bu örnek dosyasını `Order.txt` ' ye `http://www.cohowinery.com/uploads.aspx`yükler.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Bir dosyayı karşıya yüklemek ve işlemin ilerlemesini göstermek için  
  
- Kaynak dosyanın `UploadFile` konumunu ve hedef dizin konumunu DIZE veya URI olarak belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın. Bu örnek, bir Kullanıcı `Order.txt` adı `http://www.cohowinery.com/uploads.aspx` veya parola sağlamadan dosyayı karşıya yükler, karşıya yüklemenin ilerlemesini gösterir ve 500 milisaniyelik zaman aşımı aralığına sahiptir.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Bir dosyayı karşıya yüklemek için Kullanıcı adı ve parola sağlama  
  
- Kaynak dosyanın `UploadFile` konumunu ve hedef dizin konumunu bir DIZE veya URI olarak belirterek ve Kullanıcı adını ve parolayı belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın. Bu örnek, Kullanıcı adı `Order.txt` `anonymous` ve `http://www.cohowinery.com/uploads.aspx`boş bir parola sağlayarak dosyayı öğesine yükler.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durum oluşturabilir:  
  
- Yerel dosya yolu geçerli değil (<xref:System.ArgumentException>).  
  
- Kimlik doğrulama başarısız<xref:System.Security.SecurityException>oldu ().  
  
- Bağlantı zaman aşımına uğradı (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Nasıl yapılır: Dosya İndirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
