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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345628"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya İndirme

Yöntem, <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> uzak bir dosyayı karşıdan yükleyip belirli bir konuma depolamak için kullanılabilir. `ShowUI` Parametre `True`ayarlanmışsa, karşıdan yüklemenin ilerlemesini gösteren ve kullanıcıların işlemi iptal etmesine izin veren bir iletişim kutusu görüntülenir. Varsayılan olarak, aynı ada sahip varolan dosyalar üzerine yazılmamışsa; varolan dosyaların üzerine yazmak istiyorsanız, `overwrite` parametreyi ' ye `True`ayarla

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Sürücü adı geçerli<xref:System.ArgumentException>değil ( ).

- Gerekli kimlik doğrulaması sağlanmadı<xref:System.UnauthorizedAccessException> <xref:System.Security.SecurityException>(veya).

- Sunucu belirtilen `connectionTimeout` (<xref:System.TimeoutException>) içinde yanıt vermez.

- İstek Web sitesi tarafından reddedilir<xref:System.Net.WebException>( ).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1.vb dosyası Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.

### <a name="to-download-a-file"></a>Dosyayı indirmek için

- Dosyayı `DownloadFile` karşıdan yükleyerek, hedef dosyanın konumunu dize veya URI olarak belirterek ve dosyayı depolayabilmek için konumu belirtmek için yöntemi kullanın. Bu örnek, dosyayı `http://www.cohowinery.com/downloads` indirir ve `C:\Documents and Settings\All Users\Documents`aşağıdakilere `WineList.txt` kaydeder:

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Bir dosyayı indirmek için, zaman ayırma aralığı nı belirtmek

- Dosyayı `DownloadFile` indirmek, hedef dosyanın konumunu dize veya URI olarak belirtmek, dosyanın depolanacak yeri belirtmek ve zaman aralığını milisaniye cinsinden belirtmek için yöntemi kullanın (varsayılan değer 1000'dir). Bu örnek, dosyayı `http://www.cohowinery.com/downloads` karşıdan yüklenir ve 500 milisaniyelik bir zaman çıkış aralığı belirterek dosyayı `C:\Documents and Settings\All Users\Documents` `WineList.txt` kaydeder:

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Bir dosyayı indirmek için, kullanıcı adı ve parola sağlama

- Dosyayı `DownLoadFile` karşıdan yükleyerek, hedef dosyanın konumunu dize veya URI olarak belirterek ve dosyayı, kullanıcı adını ve parolayı depolayabilmek için konumu belirtmek için yöntemi kullanın. Bu örnek, `WineList.txt` dosyayı `http://www.cohowinery.com/downloads` kullanıcı adı `C:\Documents and Settings\All Users\Documents` `anonymous` ve boş bir parolayla karşıdan yükler ve kaydeder.

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > `DownLoadFile` Yöntem tarafından kullanılan FTP protokolü, parolalar da dahil olmak üzere bilgileri düz metin olarak gönderir ve hassas bilgilerin iletilmesi için kullanılmamalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Nasıl Yapılır: Karşıya Dosya Yükleme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
