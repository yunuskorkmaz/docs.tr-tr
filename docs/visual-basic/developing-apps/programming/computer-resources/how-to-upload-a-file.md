---
title: "Nasıl yapılır: Visual Basic'te dosya karşıya yükleme"
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 4e2c7a37f8d8a0fc71e0fd80d04dc5e24ad498ed
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972371"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dosya karşıya yükleme
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Yöntemi, bir dosyayı karşıya yüklemek ve uzak bir konuma depolamak için kullanılabilir. Varsa `ShowUI` parametrenin ayarlanmış `True`, karşıya yükleme ilerlemesini gösterir ve işlemi iptal etmesine izin veren bir iletişim kutusu görüntülenir.  
  
### <a name="to-upload-a-file"></a>Bir dosyayı karşıya yüklemek için  
  
-   Kullanım `UploadFile` kaynak dosya konumu ve hedef dizin konumunu bir dize veya URI'si (Tekdüzen Kaynak Tanımlayıcısı) olarak belirterek, bir dosyayı karşıya yüklemek için yöntemi. Bu örnek dosyayı yükler `Order.txt` için `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Bir dosyayı karşıya yüklemek ve işlemin ilerlemesini Göster  
  
-   Kullanım `UploadFile` kaynak dosya konumu ve hedef dizin konumunu bir dize veya URI olarak belirterek, bir dosyayı karşıya yüklemek için yöntemi. Bu örnek dosyayı yükler `Order.txt` için `http://www.cohowinery.com/uploads.aspx` bir kullanıcı adı ve parola sağlamadan karşıya yükleme ilerlemesini gösterir ve bir zaman aşımı aralığı aralığını 500 milisaniyenin vardır.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Bir kullanıcı adı ve parola sağlayan, bir dosyayı karşıya yüklemek için  
  
-   Kullanım `UploadFile` bir dize veya URI olarak kaynak dosya konumu ve hedef dizin konumunu belirtme ve kullanıcı adı ve parola belirterek bir dosyayı karşıya yüklemek için yöntemi. Bu örnek dosyayı yükler `Order.txt` için `http://www.cohowinery.com/uploads.aspx`, kullanıcı adını sağlayarak `anonymous` parolayı da boş.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar, bir özel durum oluşturabilir:  
  
-   Yerel dosya yolu geçerli değil (<xref:System.ArgumentException>).  
  
-   Kimlik doğrulaması başarısız oldu (<xref:System.Security.SecurityException>).  
  
-   Bağlantı zaman aşımına uğradı (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Nasıl yapılır: Dosya indirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Nasıl yapılır: Dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
