---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614774"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>Web 'den içerik yüklemeye izin reddediyor

#### <a name="details"></a>Ayrıntılar

. resx dosyaları, ikili biçimli giriş içerebilir. Güvenilmeyen bir konumdan indirilen bir dosyayı yüklemek için Resgen kullanmaya çalışırsanız, giriş varsayılan olarak yüklenmez.

#### <a name="suggestion"></a>Öneri

Güvenli olmayan konumlardan ikili biçimli giriş yüklemeyi gerektiren Resgen kullanıcıları, giriş dosyasındaki Web 'in işaretini kaldırabilir veya geri alma kalkisini uygulayabilir. Makine genelinde geri çevirme için aşağıdaki kayıt defteri ayarını ekleyin: [HKEY_LOCAL_MACHINE \software\microsoft.netframework\sdk] &quot; allowprocessofuntrustedresourcefiles &quot; = &quot; true&quot;

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |
