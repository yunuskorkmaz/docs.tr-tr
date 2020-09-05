---
ms.openlocfilehash: 0d38e2177377e7e9ea911071eb65aa13aa1f5900
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497044"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"Dataaçıklamalarda: dataTypeAttribute: disableRegEx" uygulama ayarı, .NET Framework 4.7.2 içinde varsayılan olarak açık

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.1 ' de, <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> kullanıcıların veri türü özniteliklerinde (, ve gibi) normal ifadelerin kullanımını devre dışı bırakmasına olanak tanıyan bir uygulama ayarı () sunuldu <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType> . Bu, belirli normal ifadeleri kullanarak hizmet reddi saldırısı olasılığa karşı güvenlik açığını azaltmaya yardımcı olur.<br/>.NET Framework 4.6.1 ' de, RegEx kullanımını devre dışı bırakmak için bu uygulama ayarı <code>false</code> Varsayılan olarak olarak ayarlanmıştır. .NET Framework 4.7.2 ile başlayarak, bu yapılandırma anahtarı <code>true</code> Varsayılan olarak, .NET Framework 4.7.2 ve üstünü hedefleyen web uygulamalarına yönelik güvenli güvenlik açığını azaltmak için varsayılan olarak ayarlanır.

#### <a name="suggestion"></a>Öneri

Web uygulamanızdaki normal ifadelerin .NET Framework 4.7.2 'e yükselttikten sonra çalışmadıysanız, <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> <code>false</code> önceki davranışa geri dönmek için ayarının değerini olarak güncelleştirebilirsiniz.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
