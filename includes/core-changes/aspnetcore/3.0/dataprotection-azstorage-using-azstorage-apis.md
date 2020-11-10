---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440430"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a>Veri koruma: DataProtection. blob 'lar yeni Azure depolama API 'Lerini kullanır

`Azure.Extensions.AspNetCore.DataProtection.Blobs`[Azure depolama kitaplıklarına](https://github.com/Azure/azure-storage-net)bağlıdır. Bu kitaplıklar derlemeleri, paketleri ve ad alanlarını yeniden adlandırdı. ASP.NET Core 3,0 ' den başlayarak, `Azure.Extensions.AspNetCore.DataProtection.Blobs` Yeni `Azure.Storage.` önekli API 'leri ve paketleri kullanır.

Azure depolama API 'Leri hakkında sorularınız için kullanın <https://github.com/Azure/azure-storage-net> . Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Paket, `WindowsAzure.Storage` NuGet paketine başvurdu.
Paket, `Microsoft.Azure.Storage.Blob` NuGet paketine başvurur.

#### <a name="new-behavior"></a>Yeni davranış

Paket, `Azure.Storage.Blob` NuGet paketine başvurur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik `Azure.Extensions.AspNetCore.DataProtection.Blobs` , önerilen Azure depolama paketlerine geçişe olanak tanır.

#### <a name="recommended-action"></a>Önerilen eylem

Hala ASP.NET Core 3,0 ile eski Azure depolama API 'Lerini kullanmanız gerekiyorsa, [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) veya [Microsoft. Azure. Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/)paketine doğrudan bir bağımlılık ekleyin. Bu paket yeni API 'ler ile birlikte yüklenebilir `Azure.Storage` .

Çoğu durumda, yükseltme yalnızca `using` Yeni ad alanlarını kullanmak için deyimlerinin değiştirilmesini içerir:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Hiçbiri

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
