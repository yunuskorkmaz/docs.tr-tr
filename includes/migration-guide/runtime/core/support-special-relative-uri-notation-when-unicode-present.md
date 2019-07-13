---
ms.openlocfilehash: c8a6870a9d34889dd8f5305035744bfc63be6af6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856982"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode olduğunda özel bir göreli URI gösterimi desteği

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Uri> artık oluşturmaz bir <xref:System.NullReferenceException> çağırırken <xref:System.Uri.TryCreate%2A> Unicode.The basit üretimi içeren belirli bir göreli URI <xref:System.NullReferenceException> aşağıdaki iki deyim ile eşdeğer olan:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Yeniden oluşturmaya <xref:System.NullReferenceException>, aşağıdakilerin doğru olması gerekir:<ul><li>URI göreli olarak ile başlayan belirtilmelidir ' http:' ve aşağıdaki ile ' / /'.</li><li>URI, yüzde olarak kodlanmış bir Unicode veya ayrılmamış simgeler içermelidir.</li></ul>|
|Öneri|Göreli URI'ler engellemek için bu davranışına göre kullanıcıların yerine belirtmelidir <xref:System.UriKind.Absolute?displayProperty=nameWithType> bir URI oluştururken.|
|`Scope`|Kenar|
|Version|4.7.2|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

