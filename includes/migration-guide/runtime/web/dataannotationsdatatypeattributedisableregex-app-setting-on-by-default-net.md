---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085529"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"Dataaçıklamalarda: dataTypeAttribute: disableRegEx" uygulama ayarı, .NET Framework 4.7.2 içinde varsayılan olarak açık

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1 ' de, kullanıcıların veri türü özniteliklerinde (<xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>ve <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>gibi) normal ifadelerin kullanımını devre dışı bırakmasına olanak tanıyan bir uygulama ayarı (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) tanıtılmıştır. Bu, belirli normal ifadeleri kullanarak hizmet reddi saldırısı olasılığa karşı güvenlik açığını azaltmaya yardımcı olur.<br/>.NET Framework 4.6.1 ' de, RegEx kullanımını devre dışı bırakmak için bu uygulama ayarı varsayılan olarak <code>false</code> olarak ayarlanmıştır. .NET Framework 4.7.2 ile başlayarak, bu yapılandırma anahtarı, .NET Framework 4.7.2 ve üstünü hedefleyen web uygulamalarına yönelik güvenli güvenlik açıklarını daha da azaltmak için varsayılan olarak <code>true</code> olarak ayarlanmıştır.|
|Öneri|Web uygulamanızdaki normal ifadelerin .NET Framework 4.7.2 'e yükselttikten sonra çalışmadıysanız, önceki davranışa geri dönmek için <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> ayarının değerini <code>false</code> olarak güncelleştirebilirsiniz.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Version|4.7.2|
|Tür|Çalışma zamanı|
