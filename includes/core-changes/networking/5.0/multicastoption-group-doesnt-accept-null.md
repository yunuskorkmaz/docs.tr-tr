---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557977"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>Multicastop. Group null bir değer kabul etmez

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> Artık değerini kabul etmez `null` . Özelliğini öğesine ayarlarsanız `null` , bir oluşturulur <xref:System.ArgumentNullException> .

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET 'in önceki sürümlerinde <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> özelliğini olarak ayarlayabilirsiniz `null` . <xref:System.Net.Sockets.MulticastOption>Daha sonra öğesine geçirilirse <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , çalışma zamanı bir oluşturur <xref:System.NullReferenceException> .

.NET 5,0 ve üzeri sürümlerde, <xref:System.ArgumentNullException> özelliği olarak ayarlarsanız oluşturulur `null` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Framework Tasarım yönergeleriyle tutarlı olması için, özelliği değeri ise oluşturmak üzere güncelleştirilmiştir <xref:System.ArgumentNullException> `null` .

#### <a name="recommended-action"></a>Önerilen eylem

' A ayarladığınızdan emin olun <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> `null` .

#### <a name="category"></a>Kategori

Ağ

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->
