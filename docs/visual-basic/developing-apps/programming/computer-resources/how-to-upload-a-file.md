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
ms.openlocfilehash: cee6811d6b6d295c28eb683c5d2f7bcbb5fe94ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401816"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme

<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>Yöntemi bir dosyayı karşıya yüklemek ve uzak bir konuma depolamak için kullanılabilir. `ShowUI`Parametresi olarak ayarlanırsa `True` , karşıya yüklemenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal etmesine izin verir.  
  
### <a name="to-upload-a-file"></a>Bir dosyayı karşıya yüklemek için  
  
- `UploadFile`Kaynak dosyanın konumunu ve hedef dizin konumunu dize veya URI (Tekdüzen Kaynak tanımlayıcısı) olarak belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın. Bu örnek dosyasını ' `Order.txt` ye yükler `http://www.cohowinery.com/uploads.aspx` .  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Bir dosyayı karşıya yüklemek ve işlemin ilerlemesini göstermek için  
  
- `UploadFile`Kaynak dosyanın konumunu ve hedef dizin konumunu dize veya URI olarak belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın. Bu örnek, `Order.txt` `http://www.cohowinery.com/uploads.aspx` bir Kullanıcı adı veya parola sağlamadan dosyayı karşıya yükler, karşıya yüklemenin ilerlemesini gösterir ve 500 milisaniyelik zaman aşımı aralığına sahiptir.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Bir dosyayı karşıya yüklemek için Kullanıcı adı ve parola sağlama  
  
- `UploadFile`Kaynak dosyanın konumunu ve hedef dizin konumunu bir dize veya URI olarak belirterek ve Kullanıcı adını ve parolayı belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın. Bu örnek `Order.txt` `http://www.cohowinery.com/uploads.aspx` , Kullanıcı adı `anonymous` ve boş bir parola sağlayarak dosyayı öğesine yükler.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durum oluşturabilir:  
  
- Yerel dosya yolu geçerli değil ( <xref:System.ArgumentException> ).  
  
- Kimlik doğrulama başarısız oldu ( <xref:System.Security.SecurityException> ).  
  
- Bağlantı zaman aşımına uğradı ( <xref:System.TimeoutException> ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Nasıl yapılır: Dosya İndirme](how-to-download-a-file.md)
- [Nasıl yapılır: Dosya Yollarını Ayrıştırma](../drives-directories-files/how-to-parse-file-paths.md)
