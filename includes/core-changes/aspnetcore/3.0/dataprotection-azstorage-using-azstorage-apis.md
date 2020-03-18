---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902064"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Veri Koruması: DataProtection.AzureStorage yeni Azure Depolama API'leri kullanır

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>Azure Depolama [kitaplıklarına](https://github.com/Azure/azure-storage-net)bağlıdır. Bu kitaplıklar derlemelerinin, paketlerinin ve ad alanlarının adını değiştirdi. Core 3.0ASP.NETdan `Microsoft.AspNetCore.DataProtection.AzureStorage` başlayarak `Microsoft.Azure.Storage.`yeni önceden belirlenmiş API'leri ve paketleri kullanır.

Azure Depolama API'leri ile <https://github.com/Azure/azure-storage-net>ilgili sorularınız için . Bu konuda tartışma için [dotnet/aspnetcore#8472'ye](https://github.com/dotnet/aspnetcore/issues/8472)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Paket, NuGet `WindowsAzure.Storage` paketine atıfta bulunarak başvuruda bulunarak, bu pakete atıfta bulunmaktadır.

#### <a name="new-behavior"></a>Yeni davranış

Paket NuGet `Microsoft.Azure.Storage.Blob` paketine başvurur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, önerilen Azure Depolama paketlerine geçiş yapılmasına olanak tanır. `Microsoft.AspNetCore.DataProtection.AzureStorage`

#### <a name="recommended-action"></a>Önerilen eylem

Core 3.0'ASP.NET eski Azure Depolama API'lerini kullanmaya devam ederseniz, [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) paketine doğrudan bağımlılık ekleyin. Bu paket, yeni `Microsoft.Azure.Storage` API'lerin yanına yüklenebilir.

Çoğu durumda, yükseltme yalnızca yeni `using` ad alanlarını kullanmak için deyimleri değiştirmeyi içerir:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
