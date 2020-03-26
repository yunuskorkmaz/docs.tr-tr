---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291661"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure: Microsoft tarafından önceden belirlenmiş Azure tümleştirme paketleri kaldırıldı

ASP.NET `Microsoft.*` Core ve Azure SDK'ları arasında tümleştirme sağlayan aşağıdaki paketler ASP.NET Core 5.0'a dahil değildir:

* [Azure Key Vault'u](/azure/key-vault/) [Yapılandırma sistemine](/aspnet/core/fundamentals/configuration/)entegre eden [Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/).
* Azure Key Vault'u [ASP.NET Çekirdek Veri Koruma sistemine](/aspnet/core/security/data-protection/introduction)entegre eden [Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/).
* [Azure Blob Depolama'yı](/azure/storage/blobs/) ASP.NET Çekirdek Veri Koruma sistemine entegre eden [Microsoft.AspNetCore.DataProtection.AzureStorage.](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)

Bu konuda tartışma için [dotnet/aspnetcore#19570'e](https://github.com/dotnet/aspnetcore/issues/19570)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

5.0 Önizleme 1

#### <a name="old-behavior"></a>Eski davranış

Paketler `Microsoft.*` Azure hizmetlerini Yapılandırma ve Veri Koruma API'leriyle bütünleştirdi.

#### <a name="new-behavior"></a>Yeni davranış

Yeni `Azure.*` paketler Azure hizmetlerini Yapılandırma ve Veri Koruma API'leriyle tümleştirir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik yapıldı çünkü `Microsoft.*` paketler:

* Azure SDK'nın eski sürümlerini kullanma. Azure SDK'nın yeni sürümlerinde kesme değişiklikleri içerdiğinden basit güncelleştirmeler mümkün değildi.
* .NET Core yayın programına bağlı. Paketlerin sahipliğini Azure SDK ekibine aktarmak, Azure SDK güncelleştirildikçe paket güncelleştirmelerine olanak tanır.

#### <a name="recommended-action"></a>Önerilen eylem

core 2.1 veya daha sonraki ASP.NET `Microsoft.*` projelerde, eskiyi yeni `Azure.*` paketlerle değiştirin.

| Eski | Yeni |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure.AspNetCore.DataProtection.Keys](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure.AspNetCore.DataProtection.Blobs](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.Configuration.Secrets](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

Yeni paketler, Azure SDK'nın değişiklikleri kesmeyi içeren yeni bir sürümünü kullanır. Genel kullanım desenleri değişmedi. Bazı aşırı yüklemeler ve seçenekler, temel Azure SDK API'lerinde ki değişikliklere uyum sağlamak için farklılık gösterebilir.

Eski paketler:

* .NET Core 2.1 ve 3.1 ömrü boyunca ASP.NET Core ekibi tarafından desteklenebilir.
* .NET 5'e dahil edilmeyin.

Projenizi .NET 5'e yükseltirken, `Azure.*` desteği korumak için paketlere geçiş yap.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
