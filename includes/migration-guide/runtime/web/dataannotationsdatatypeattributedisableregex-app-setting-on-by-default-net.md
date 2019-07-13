---
ms.openlocfilehash: b021de74509b6d9ba77678d3105e0f7bb406f79d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856942"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"dataAnnotations:dataTypeAttribute:disableRegEx" uygulama ayarı varsayılan olarak .NET Framework 4.7.2 açıktır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1, bir uygulama ayarı (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) sunulan veri türü özniteliklerini normal ifadeler kullanımını devre dışı bırakmak kullanıcılara izin verir (gibi <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, ve <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Bu, belirli bir normal ifadeler kullanarak bir hizmet reddi saldırısı olasılığını önleme gibi güvenlik açığı azaltmaya yardımcı olur.<br/>.NET Framework 4.6.1, normal ifade kullanımı devre dışı bırakmak için bu uygulama ayarının ayarlandı <code>false</code> varsayılan olarak. .NET Framework ile 4.7.2 başlamanızı, bu yapılandırma anahtarı ayarlanır <code>true</code> daha da güvenli güvenlik açığı 4.7.2 .NET Framework'ü hedefleyen web uygulamaları ve üzeri azaltmak için varsayılan.|
|Öneri|Normal ifadelerde, web uygulamanızın .NET Framework 4.7.2 yükselttikten sonra çalışmıyor bulursanız, değerini güncelleştirebilirsiniz <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> ayarını <code>false</code> önceki davranışa dönmek.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.7.2|
|Type|Çalışma zamanı|

