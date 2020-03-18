---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451906"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage.Version varsayılan değeri 1.1 olarak değiştirildi

Özelliğin <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> varsayılan değeri 2,0'dan 1,1'e değiştirildi.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 1.0 ile 2.0 arasında, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özelliğin varsayılan değeri 1.1'dir. .NET Core 2.1 ile başlayarak 2.1 olarak değiştirildi.

.NET Core 3.0 ile başlayarak, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> özellik tarafından döndürülen varsayılan sürüm numarası bir kez daha 1.1'dir.

#### <a name="recommended-action"></a>Önerilen eylem

Varsayılan değeri 2.0 olarak <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> döndüren özellik bağlıysa kodunuzu güncelleştirin.

#### <a name="category"></a>Kategori

Ağ

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
