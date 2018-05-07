---
title: "Nasıl Yapılır: Visual Basic'te Dosya İndirme"
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: b0dc95674e17a7aba9b04a8b7e0b82c9c97c4180
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya İndirme
<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Yöntemi, bir uzak dosya karşıdan yüklemek ve belirli bir konuma depolamak için kullanılabilir. Varsa `ShowUI` parametrenin ayarlanmış `True`, yükleme ilerlemesini gösteren ve kullanıcıların işlemi iptal etmek bir iletişim kutusu görüntülenir. Varsayılan olarak, aynı ada sahip var olan dosyaların üzerine yazılmaz; var olan dosyaların üzerine yazmak istiyorsanız, Ayarla `overwrite` parametresi `True`.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Sürücü adı geçerli değil (<xref:System.ArgumentException>).  
  
-   Gerekli kimlik doğrulaması olmayan sağlanmış (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).  
  
-   Sunucu belirtilen içinde yanıt vermezse `connectionTimeout` (<xref:System.TimeoutException>).  
  
-   İstek Web sitesi tarafından reddedilir (<xref:System.Net.WebException>).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
### <a name="to-download-a-file"></a>Bir dosyayı indirmek için  
  
-   Kullanım `DownloadFile` yöntemi bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosyasının depolanacağı konumu belirtme dosyasını indirin. Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Bir zaman aşımı aralığı belirterek, bir dosyayı indirmek için  
  
-   Kullanım `DownloadFile` yöntemi bir dize veya URI olarak hedef dosyanın konumunu belirtme, dosyasının depolanacağı konumu belirtme ve zaman aşımı aralığı (varsayılan değer 1000) milisaniye cinsinden belirten dosyasını indirin. Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, 500 milisaniye zaman aşımı aralığı belirtme:  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Bir kullanıcı adı ve parola sağlayarak bir dosyayı indirmek için  
  
-   Kullanım `DownLoadFile` yöntemi bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosya, kullanıcı adı ve parola depolanacağı konumu belirtme dosyasını indirin. Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, kullanıcı adı ile `anonymous` ve boş bir parola.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  Tarafından kullanılan FTP protokolünü `DownLoadFile` yöntemi bilgilerini, parolalar düz metin olarak gönderir ve hassas bilgiler iletmek için kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [Nasıl Yapılır: Karşıya Dosya Yükleme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
