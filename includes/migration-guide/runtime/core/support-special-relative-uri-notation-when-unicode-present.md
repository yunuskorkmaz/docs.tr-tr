---
ms.openlocfilehash: 34d7395e72f6ef252ac68366bcd346cd8d464036
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236152"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode olduğunda özel bir göreli URI gösterimi desteği

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Uri> artık oluşturmaz bir <xref:System.NullReferenceException> çağırırken <xref:System.Uri.TryCreate%2A> Unicode.The basit üretimi içeren belirli bir göreli URI <xref:System.NullReferenceException> aşağıdaki iki deyim ile eşdeğer olan:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Yeniden oluşturmaya <xref:System.NullReferenceException>, aşağıdakilerin doğru olması gerekir:<ul><li>URI göreli olarak ile başlayan belirtilmelidir ' http:' ve aşağıdaki ile ' / /'.</li><li>URI, yüzde olarak kodlanmış bir Unicode veya ayrılmamış simgeler içermelidir.</li></ul>|
|Öneri|Göreli URI'ler engellemek için bu davranışına göre kullanıcıların yerine belirtmelidir <xref:System.UriKind.Absolute?displayProperty=nameWithType> bir URI oluştururken.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
