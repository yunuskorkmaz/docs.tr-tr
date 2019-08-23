---
title: 'Nasıl yapılır: Visual Basic bir dosyayı indirin'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 9986a784e73f12698281f17a9d8e022e806504cb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957827"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Nasıl yapılır: Visual Basic bir dosyayı indirin
Yöntemi <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> , uzak bir dosyayı indirmek ve belirli bir konuma depolamak için kullanılabilir. `ShowUI` Parametresi olarak`True`ayarlandıysa, indirmenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal edebilmesine izin verir. Varsayılan olarak, aynı ada sahip var olan dosyaların üzerine yazılmaz; Varolan dosyaların üzerine yazmak istiyorsanız `overwrite` parametresini olarak `True`ayarlayın.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Sürücü adı geçerli değil (<xref:System.ArgumentException>).  
  
- Gerekli kimlik doğrulaması sağlanmadı (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).  
  
- Sunucu belirtilen `connectionTimeout` (<xref:System.TimeoutException>) içinde yanıt vermiyor.  
  
- İstek Web sitesi (<xref:System.Net.WebException>) tarafından reddedildi.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
> Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
### <a name="to-download-a-file"></a>Bir dosyayı indirmek için  
  
- Hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu belirterek dosyayı indirmek için yönteminikullanın.`DownloadFile` Bu örnek dosyasını `WineList.txt` konumundan `http://www.cohowinery.com/downloads` indirir ve öğesine `C:\Documents and Settings\All Users\Documents`kaydeder:  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Bir dosya indirmek için bir zaman aşımı aralığı belirtme  
  
- Dosyayı indirmek için yöntemini kullanın, hedef dosyanın konumunu bir dize veya URI olarak belirterek, dosyanın kaydedileceği konumu belirterek ve zaman aşımı aralığını milisaniye cinsinden (varsayılan olarak 1000) belirterek. `DownloadFile` Bu örnek, ' dan `WineList.txt` `http://www.cohowinery.com/downloads` dosyayı indirir ve 500 milisaniyelik bir zaman aşımı aralığı belirterek öğesine `C:\Documents and Settings\All Users\Documents`kaydeder:  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Bir dosyayı indirmek için Kullanıcı adı ve parola sağlama  
  
- Hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu, Kullanıcı adını ve parolayı belirterek dosyayı indirmek için yönteminikullanın.`DownLoadFile` Bu örnek `WineList.txt` , dosyasını `C:\Documents and Settings\All Users\Documents`' dan `http://www.cohowinery.com/downloads` indirir ve Kullanıcı adı `anonymous` ve boş bir parolayla kaydeder.  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  `DownLoadFile` Yöntemi tarafından kullanılan FTP protokolü, parolalar da dahil olmak üzere bilgileri düz metin olarak gönderir ve hassas bilgilerin iletilmesi için kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Nasıl yapılır: Karşıya dosya yükleme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Nasıl yapılır: Dosya yollarını Ayrıştır](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
