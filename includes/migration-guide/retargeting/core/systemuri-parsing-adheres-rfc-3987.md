---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617279"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>System. Uri ayrıştırma, RFC 3987 ' e uyar

#### <a name="details"></a>Ayrıntılar

URI ayrıştırma .NET Framework 4,5 ' de çeşitli yollarla değiştirilmiştir. Ancak, bu değişikliklerin yalnızca 4,5 .NET Framework kod hedeflemesi etkilediğini unutmayın. Bir ikili .NET Framework 4,0 hedefliyorsa, eski davranış gözlenecek. .NET Framework 4,5 ' de URI ayrıştırmasında yapılan değişiklikler şunları içerir:

- URI ayrıştırma, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi gerçekleştirir.
- Unicode normalleştirme biçimi C yalnızca URI 'nin ana bilgisayar bölümünde gerçekleştirilir.
- Geçersiz mailto: URI 'Ler şimdi bir özel duruma neden olur.
- Bir yol kesiminin sonundaki sondaki noktalar artık korunur.
- `file://`URI 'Ler karakterden kaçmaz `?` .
- İle Unicode denetim `U+0080` karakterleri `U+009F` desteklenmez.
- Virgül karakterleri `,` veya `%2c` otomatik olarak geri atlanmaz.

#### <a name="suggestion"></a>Öneri

Eski .NET Framework 4,0 URI ayrıştırma semantiği gerekliyse (genellikle bunlar), .NET Framework 4,0 ' i hedefleyerek kullanılabilirler. Bu, <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> derlemede bir veya ' Proje Özellikleri ' sayfasında Visual Studio 'nun proje sistem kullanıcı arabirimi aracılığıyla gerçekleştirilebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
