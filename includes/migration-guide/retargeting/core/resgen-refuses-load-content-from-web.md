---
ms.openlocfilehash: 6cdd410cc818c2c0a993a364e550f5f92ed6a821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981869"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>İçeriği Web'den yüklemek ResGen reddediyor

|   |   |
|---|---|
|Ayrıntılar|.resx dosyalarını ikili biçimlendirilmiş bir giriş içeriyor olabilir. Resgen, güvenilmeyen bir konumdan indirilen dosya yüklemek için kullanmayı denerseniz, varsayılan olarak giriş yükleme başarısız olur.|
|Öneri|İkili biçimlendirilmiş bir giriş güvenilmeyen konumlardan gerektiren Resgen kullanıcılar web işareti giriş dosyasından kaldırın veya geri çevirme quirk uygulayın. Makine geniş çevirme quirk uygulamak için aşağıdaki kayıt defteri ayarını ekleyin: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|
