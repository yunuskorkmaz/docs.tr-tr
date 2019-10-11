---
ms.openlocfilehash: b50a108d2efbfd3da0d690cb02537a12f766b26b
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237479"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage. Version öğesinin varsayılan değeri 1,1 olarak değiştirildi 

@No__t-0 özelliğinin varsayılan değeri 2,0 ' den 1,1 ' e değişmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3.0

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 1,0 ile 2,0 arasında, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliğinin varsayılan değeri 1,1 ' dir. .NET Core 2,1 ile başlayarak, 2,1 olarak değiştirilmiştir. 

.NET Core 3,0 ile başlayarak, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliği tarafından döndürülen varsayılan sürüm numarası bir kez daha 1,1.
 
#### <a name="recommended-action"></a>Önerilen eylem

Varsayılan 2,0 değerini döndüren <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliğine bağımlıysa, kodunuzu güncelleştirin.

#### <a name="category"></a>Kategori

Ağ Oluşturma

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

