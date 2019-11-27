---
title: 'Nasıl Yapılır: Dosya İndirme'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 4923feb46ff638de9514a4d70fc00367491a6f44
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345628"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya İndirme

<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> yöntemi, uzak bir dosyayı indirmek ve belirli bir konuma depolamak için kullanılabilir. `ShowUI` parametresi `True`olarak ayarlanırsa, indirmenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal edebilmesine izin verir. Varsayılan olarak, aynı ada sahip var olan dosyaların üzerine yazılmaz; Varolan dosyaların üzerine yazmak istiyorsanız `overwrite` parametresini `True`olarak ayarlayın.

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Sürücü adı geçerli değil (<xref:System.ArgumentException>).

- Gerekli kimlik doğrulaması sağlanmadı (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).

- Sunucu belirtilen `connectionTimeout` (<xref:System.TimeoutException>) içinde yanıt vermiyor.

- İstek Web sitesi tarafından reddedildi (<xref:System.Net.WebException>).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.

### <a name="to-download-a-file"></a>Bir dosyayı indirmek için

- Hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu belirterek dosyayı indirmek için `DownloadFile` yöntemini kullanın. Bu örnek, `http://www.cohowinery.com/downloads` `WineList.txt` dosyayı indirir ve `C:\Documents and Settings\All Users\Documents`kaydeder:

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Bir dosya indirmek için bir zaman aşımı aralığı belirtme

- Dosyayı indirmek için `DownloadFile` yöntemi kullanın, hedef dosyanın konumunu bir dize veya URI olarak belirterek, dosyanın kaydedileceği konumu belirterek ve zaman aşımı aralığını milisaniye cinsinden (varsayılan: 1000) belirterek. Bu örnek, `http://www.cohowinery.com/downloads` `WineList.txt` dosyayı indirir ve 500 milisaniyelik zaman aşımı aralığını belirterek `C:\Documents and Settings\All Users\Documents`kaydeder:

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Bir dosyayı indirmek için Kullanıcı adı ve parola sağlama

- Dosyayı indirmek için `DownLoadFile` yöntemini kullanın, hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu, Kullanıcı adını ve parolayı belirtin. Bu örnek, `http://www.cohowinery.com/downloads` `WineList.txt` dosyayı indirir ve Kullanıcı adı `anonymous` ve boş bir parolayla `C:\Documents and Settings\All Users\Documents`kaydeder.

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > `DownLoadFile` yöntemi tarafından kullanılan FTP protokolü, parolalar da dahil olmak üzere bilgileri düz metin olarak gönderir ve hassas bilgilerin iletilmesi için kullanılmamalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Nasıl Yapılır: Karşıya Dosya Yükleme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
