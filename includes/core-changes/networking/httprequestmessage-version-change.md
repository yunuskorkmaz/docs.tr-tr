---
ms.openlocfilehash: 78d2ec6fb505573ad36d55a9ca0a20452b7fa244
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002868"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage. Version öğesinin varsayılan değeri 1,1 olarak değiştirildi 

@No__t-0 özelliğinin varsayılan değeri 2,0 ' den 1,1 ' e değişmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3.0

#### <a name="details"></a>Ayrıntılar

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

