---
ms.openlocfilehash: f17efc89b738a9fd20cc687de1dae01a44664271
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621391"
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
