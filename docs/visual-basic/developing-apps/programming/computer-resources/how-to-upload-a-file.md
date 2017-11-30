---
title: "Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a0fab9b812ddff1f56e9fa203bd297fd70bc47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Yöntemi, bir dosyayı karşıya yükleme ve uzak bir konuma depolamak için kullanılabilir. Varsa `ShowUI` parametrenin ayarlanmış `True`, karşıya yükleme ilerlemesini gösterir ve işlemi iptal etmek kullanıcıların sağlayan bir iletişim kutusu görüntülenir.  
  
### <a name="to-upload-a-file"></a>Bir dosyayı karşıya yüklemek için  
  
-   Kullanım `UploadFile` bir dize veya URI'yi (Tekdüzen Kaynak Tanımlayıcısı) olarak kaynak dosya konumu ve hedef dizin konumunu belirten bir dosyayı karşıya yüklemeyi yöntemi. Bu örnek dosya karşıya yükleme `Order.txt` için `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Bir dosyayı karşıya yükleyin ve işlemin ilerlemesini Göster  
  
-   Kullanım `UploadFile` bir dize veya URI olarak kaynak dosya konumu ve hedef dizin konumunu belirten bir dosyayı karşıya yüklemeyi yöntemi. Bu örnek dosya karşıya yükleme `Order.txt` için `http://www.cohowinery.com/uploads.aspx` bir kullanıcı adı veya parola girmeden karşıya yükleme ilerlemesini gösterir ve bir zaman aşımı aralığı (500 milisaniye olarak) sahiptir.  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Bir kullanıcı adı ve parola sağlayarak bir dosyayı karşıya yüklemek için  
  
-   Kullanım `UploadFile` bir dize veya URI olarak kaynak dosya konumu ve hedef dizin konumunu belirtme ve kullanıcı adı ve parola belirterek bir dosyayı karşıya yüklemeyi yöntemi. Bu örnek dosya karşıya yükleme `Order.txt` için `http://www.cohowinery.com/uploads.aspx`, kullanıcı adını sağlayarak `anonymous` ve boş bir parola.  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar, bir özel durum:  
  
-   Yerel dosya yolu geçerli değil (<xref:System.ArgumentException>).  
  
-   Kimlik doğrulama başarısız oldu (<xref:System.Security.SecurityException>).  
  
-   Bağlantı zaman aşımına uğradı (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>  
 [Nasıl yapılır: dosya indirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)  
 [Nasıl yapılır: dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
