---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567747"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage. Version öğesinin varsayılan değeri 1,1 olarak değiştirildi

<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliğinin varsayılan değeri 2,0 ' den 1,1 ' e değişmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3.0

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 1,0 ile 2,0 arasında, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliğinin varsayılan değeri 1,1 ' dir. .NET Core 2,1 ile başlayarak, 2,1 olarak değiştirilmiştir.

.NET Core 3,0 ile başlayarak, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliği tarafından döndürülen varsayılan sürüm numarası bir kez daha 1,1.

#### <a name="recommended-action"></a>Önerilen eylem

Varsayılan 2,0 değerini döndüren <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliğine bağımlıysa kodunuzu güncelleştirin.

#### <a name="category"></a>Kategori

Ağ Oluşturma

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

