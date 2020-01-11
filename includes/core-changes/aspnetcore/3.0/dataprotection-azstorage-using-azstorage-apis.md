---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902064"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Veri koruma: DataProtection. AzureStorage yeni Azure depolama API 'Lerini kullanır

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>, [Azure depolama kitaplıklarına](https://github.com/Azure/azure-storage-net)bağlıdır. Bu kitaplıklar derlemeleri, paketleri ve ad alanlarını yeniden adlandırdı. ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.DataProtection.AzureStorage` yeni `Microsoft.Azure.Storage.`ön eki olan API 'Leri ve paketleri kullanır.

Azure depolama API 'Leri hakkında sorularınız için <https://github.com/Azure/azure-storage-net>kullanın. Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Paket, `WindowsAzure.Storage` NuGet paketine başvurdu.

#### <a name="new-behavior"></a>Yeni davranış

Paket, `Microsoft.Azure.Storage.Blob` NuGet paketine başvurur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, `Microsoft.AspNetCore.DataProtection.AzureStorage` önerilen Azure depolama paketlerine geçiş yapmasına olanak tanır.

#### <a name="recommended-action"></a>Önerilen eylem

Hala ASP.NET Core 3,0 ile eski Azure depolama API 'Lerini kullanmanız gerekiyorsa, [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) paketine doğrudan bir bağımlılık ekleyin. Bu paket, yeni `Microsoft.Azure.Storage` API 'Leri ile birlikte yüklenebilir.

Çoğu durumda, yükseltme yalnızca `using` deyimlerinin yeni ad alanlarını kullanacak şekilde değiştirilmesini içerir:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
