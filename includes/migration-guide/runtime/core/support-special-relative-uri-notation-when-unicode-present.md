---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997736"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode mevcut olduğunda özel göreli URI gösterimini destekleme

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Uri>, artık Unicode içeren belirli <xref:System.NullReferenceException> göreli URI <xref:System.Uri.TryCreate%2A> 'ler üzerinde çağrılırken bir oluşturmaz. En basit üretilmesi <xref:System.NullReferenceException> , iki deyimle denk olacak şekilde aşağıda verilmiştir:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException>Öğesini yeniden oluşturmak için aşağıdaki öğelerin doğru olması gerekir:<ul><li>URI, ' http: ' ile bir ön bekleyen olarak belirtilmelidir ve '//' ile takip edilmez.</li><li>URI, yüzde kodlamalı Unicode veya ayrılmamış simgeler içermelidir.</li></ul>|
|Öneri|Göreli URI 'lara izin vermemek için bu davranışa bağlı olarak, bir <xref:System.UriKind.Absolute?displayProperty=nameWithType> URI oluşturma sırasında belirtilmelidir.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
