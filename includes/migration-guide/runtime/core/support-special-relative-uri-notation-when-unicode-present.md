---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997736"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode mevcut olduğunda özel göreli URI gösterimini destekleyin

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Uri>unicode içeren <xref:System.NullReferenceException> belirli <xref:System.Uri.TryCreate%2A> göreli URI'leri ararken artık bir atmaz. En basit çoğaltma aşağıdaki <xref:System.NullReferenceException> gibidir, iki ifade eşdeğer olmak:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Yeniden oluşturmak <xref:System.NullReferenceException>için aşağıdaki öğelerin doğru olması gerekir:<ul><li>URI'nin 'http:' ile önleyerek ve '//' ile takip etmeyerek göreceli olarak belirtilmelidir.</li><li>URI yüzde kodlanmış Unicode veya ayrılmamış semboller içermelidir.</li></ul>|
|Öneri|Bu davranışa bağlı olarak, göreceli ÜR'lere <xref:System.UriKind.Absolute?displayProperty=nameWithType> izin vermemek yerine BIR URI oluştururken belirtmeleri gerekir.|
|Kapsam|Edge|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
