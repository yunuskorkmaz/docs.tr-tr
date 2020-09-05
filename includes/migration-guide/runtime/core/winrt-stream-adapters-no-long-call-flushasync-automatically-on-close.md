---
ms.openlocfilehash: 2b4f35fe15f806897e5e4d85ee774b2e4572d974
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497163"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT akış bağdaştırıcıları otomatik olarak kapanmaz FlushAsync

#### <a name="details"></a>Ayrıntılar

Windows Mağazası uygulamalarında Windows Çalışma Zamanı akış bağdaştırıcıları artık Dispose yönteminden FlushAsync yöntemini çağırmaz.

#### <a name="suggestion"></a>Öneri

Bu değişiklik saydam olmalıdır. Geliştiriciler aşağıdakine benzer bir kod yazarak önceki davranışı geri yükleyebilir:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Geçirgen|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
