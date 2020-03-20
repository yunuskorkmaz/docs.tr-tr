---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73085529"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"dataAnnotations:dataTypeAttribute:disableRegEx" uygulama ayarı varsayılan olarak .NET Framework 4.7.2'de

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1'de,<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>kullanıcıların veri türü özniteliklerinde <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>(, ve) <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>normal ifadelerin kullanımını devre dışı bmesine olanak tanıyan bir uygulama ayarı () <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>sunulmuştur. Bu, belirli düzenli ifadeler kullanarak Hizmet Reddi saldırısı olasılığını önlemek gibi güvenlik açığını azaltmaya yardımcı olur.<br/>.NET Framework 4.6.1'de, RegEx kullanımını devre dışı <code>false</code> bırakmak için bu uygulama ayarı varsayılan olarak ayarlanmıştır. .NET Framework 4.7.2 ile başlayarak, bu <code>true</code> config anahtarı varsayılan olarak .NET Framework 4.7.2 ve üzeri web uygulamaları için güvenli güvenlik açığını daha da azaltacak şekilde ayarlanır.|
|Öneri|Web uygulamanızdaki normal ifadelerin .NET Framework 4.7.2'ye yükselttikten sonra çalışmadığını fark ederseniz, <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> önceki <code>false</code> davranışa geri dönmek için ayar değerini güncelleştirebilirsiniz.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|
