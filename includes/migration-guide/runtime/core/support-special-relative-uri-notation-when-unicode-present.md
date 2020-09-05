---
ms.openlocfilehash: 3c32d2e13447f8fd9aa6b185b5fc7e60f9e1bb61
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497236"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode mevcut olduğunda özel göreli URI gösterimini destekleme

#### <a name="details"></a>Ayrıntılar

<xref:System.Uri> , artık <xref:System.NullReferenceException> <xref:System.Uri.TryCreate%2A> Unicode içeren belirli göreli URI 'ler üzerinde çağrılırken bir oluşturmaz. En basit üretilmesi, <xref:System.NullReferenceException> iki deyimle denk olacak şekilde aşağıda verilmiştir:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException>Öğesini yeniden oluşturmak için aşağıdaki öğelerin doğru olması gerekir:<ul><li>URI, ' http: ' ile bir ön bekleyen olarak belirtilmelidir ve '//' ile takip edilmez.</li><li>URI, yüzde kodlamalı Unicode veya ayrılmamış simgeler içermelidir.</li></ul>

#### <a name="suggestion"></a>Öneri

Göreli URI 'lara izin vermemek için bu davranışa bağlı olarak, <xref:System.UriKind.Absolute?displayProperty=nameWithType> bir URI oluşturma sırasında belirtilmelidir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)`
- `M:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)`
- `M:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)`

-->
