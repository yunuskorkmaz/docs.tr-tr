---
title: 'Nasıl yapılır: Dosya İndirme'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: a5b379da00656f65476e4d9504457bf8b464beac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411661"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Dosya İndirme

<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>Yöntemi, uzak bir dosyayı indirmek ve belirli bir konuma depolamak için kullanılabilir. `ShowUI`Parametresi olarak ayarlandıysa `True` , indirmenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal edebilmesine izin verir. Varsayılan olarak, aynı ada sahip var olan dosyaların üzerine yazılmaz; Varolan dosyaların üzerine yazmak istiyorsanız `overwrite` parametresini olarak ayarlayın `True` .

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Sürücü adı geçerli değil ( <xref:System.ArgumentException> ).

- Gerekli kimlik doğrulaması sağlanmadı ( <xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException> ).

- Sunucu belirtilen () içinde yanıt vermiyor `connectionTimeout` <xref:System.TimeoutException> .

- İstek Web sitesi () tarafından reddedildi <xref:System.Net.WebException> .

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.

### <a name="to-download-a-file"></a>Bir dosyayı indirmek için

- `DownloadFile`Hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu belirterek dosyayı indirmek için yöntemini kullanın. Bu örnek dosyasını konumundan indirir `WineList.txt` `http://www.cohowinery.com/downloads` ve öğesine kaydeder `C:\Documents and Settings\All Users\Documents` :

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Bir dosya indirmek için bir zaman aşımı aralığı belirtme

- `DownloadFile`Dosyayı indirmek için yöntemini kullanın, hedef dosyanın konumunu bir dize veya URI olarak belirterek, dosyanın kaydedileceği konumu belirterek ve zaman aşımı aralığını milisaniye cinsinden (varsayılan olarak 1000) belirterek. Bu örnek, `WineList.txt` ' dan dosyayı indirir `http://www.cohowinery.com/downloads` ve `C:\Documents and Settings\All Users\Documents` 500 milisaniyelik bir zaman aşımı aralığı belirterek öğesine kaydeder:

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Bir dosyayı indirmek için Kullanıcı adı ve parola sağlama

- `DownLoadFile`Hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu, Kullanıcı adını ve parolayı belirterek dosyayı indirmek için yöntemini kullanın. Bu örnek, dosyasını `WineList.txt` ' dan indirir `http://www.cohowinery.com/downloads` ve `C:\Documents and Settings\All Users\Documents` Kullanıcı adı `anonymous` ve boş bir parolayla kaydeder.

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > Yöntemi tarafından kullanılan FTP protokolü, `DownLoadFile` parolalar da dahil olmak üzere bilgileri düz metin olarak gönderir ve hassas bilgilerin iletilmesi için kullanılmamalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Nasıl yapılır: Karşıya Dosya Yükleme](how-to-upload-a-file.md)
- [Nasıl yapılır: Dosya Yollarını Ayrıştırma](../drives-directories-files/how-to-parse-file-paths.md)
