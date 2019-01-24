---
title: "Nasıl yapılır: Visual Basic'te dosya indirme"
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 435dfe497cde5a08bce8825eaf6fa73daab4348b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671193"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dosya indirme
<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Yöntemi, uzak bir dosyaya indirin ve belirli bir konuma depolamak için kullanılabilir. Varsa `ShowUI` parametrenin ayarlanmış `True`, indirme işleminin ilerleme durumunu gösterir ve kullanıcı işlemi iptal etme iletişim kutusu görüntülenir. Varsayılan olarak, aynı ada sahip mevcut dosyaların üzerine yazılmaz; Varolan dosyaların üzerine yazmak istiyorsanız ayarlayın `overwrite` parametresi `True`.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Sürücü adı geçerli değil (<xref:System.ArgumentException>).  
  
-   Gerekli kimlik doğrulama yok sağlanmış (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).  
  
-   Sunucu belirtilen içinde yanıt vermezse `connectionTimeout` (<xref:System.TimeoutException>).  
  
-   İstek Web sitesi tarafından reddedilir (<xref:System.Net.WebException>).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
### <a name="to-download-a-file"></a>Bir dosyayı indirmek için  
  
-   Kullanım `DownloadFile` bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosyasının depolanacağı konumu belirtin dosyayı indirmek için yöntemi. Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Bir zaman aşımı aralığı belirterek, bir dosyayı indirmek için  
  
-   Kullanım `DownloadFile` zaman aşımı aralığı (varsayılan değer 1000) milisaniye cinsinden belirten bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosyasının depolanacağı konumu belirtme dosyasını indirmek için yöntemi. Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, aralığını 500 milisaniyenin bir zaman aşımı aralığı belirtme:  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Bir kullanıcı adı ve parola sağlayan, bir dosyayı indirmek için  
  
-   Kullanım `DownLoadFile` bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosya, kullanıcı adı ve parola depolanacağı konumu belirtin dosyayı indirmek için yöntemi. Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, kullanıcı adıyla `anonymous` parolayı da boş.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  Tarafından kullanılan FTP protokolünü `DownLoadFile` yöntemi bilgilerini, parolaları düz metin olarak gönderir ve hassas bilgileri aktarmak için kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Nasıl yapılır: Bir dosyayı karşıya yükleyin](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Nasıl yapılır: Dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
