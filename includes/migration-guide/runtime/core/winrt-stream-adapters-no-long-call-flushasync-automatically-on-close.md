---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620597"
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
