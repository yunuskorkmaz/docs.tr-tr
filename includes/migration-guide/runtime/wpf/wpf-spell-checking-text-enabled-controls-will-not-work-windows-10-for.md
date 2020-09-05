---
ms.openlocfilehash: 6d7f998cda6326e1f584713576a0aa27b3a68655
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497128"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>Metin özellikli denetimlerde WPF yazım denetimi, işletim sisteminin giriş dili listesinde olmayan diller için Windows 10 ' da çalışmaz

#### <a name="details"></a>Ayrıntılar

Windows 10 ' da çalışırken, platform yazım denetimi özellikleri yalnızca giriş dilleri listesinde bulunan diller için kullanılabilir olduğundan, yazım denetleyicisi WPF metin özellikli denetimler için çalışmayabilir. Windows 10 ' da, kullanılabilir klavyeler listesine bir dil eklendiğinde, Windows otomatik olarak yazım denetimi özellikleri sağlayan ilgili bir Isteğe bağlı Özellik (FOD) paketini indirir ve yükler. Dili giriş dilleri listesine ekleyerek, yazım denetleyicisi desteklenecektir.

#### <a name="suggestion"></a>Öneri

Yazım denetimi yapılacak dilin veya metnin, Windows 10 ' da çalışmak üzere yazım denetimi yapmak için bir giriş dili olarak eklenmesi gerektiğini unutmayın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
