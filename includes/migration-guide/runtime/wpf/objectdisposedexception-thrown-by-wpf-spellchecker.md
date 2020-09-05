---
ms.openlocfilehash: 3244913e06a744dafc4440f824ebe6bed25b8dd1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496299"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>WPF yazım denetleyicisi tarafından oluşturulan ObjectDisposedException

#### <a name="details"></a>Ayrıntılar

WPF uygulamaları <xref:System.ObjectDisposedException?displayProperty=fullName> , yazım denetleyicisi tarafından oluşturulan uygulama kapatılırken zaman zaman kilitleniyor. Bu, özel durumu düzgün şekilde işleyerek ve bu nedenle uygulamaların artık etkilenmemesi sağlanarak .NET Framework 4,7 WPF 'de düzeltilir. Bu, zaman bir hata ayıklayıcı altında çalışan uygulamalarda devam eden ilk şans özel durumların gözlemlendiği unutulmamalıdır.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,7 ' ye yükseltin

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
