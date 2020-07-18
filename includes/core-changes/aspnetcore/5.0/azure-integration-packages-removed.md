---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416254"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure: Microsoft 'un ön eki olan Azure tümleştirme paketleri kaldırıldı

`Microsoft.*`ASP.NET Core ve Azure SDK 'ları arasında tümleştirme sağlayan aşağıdaki paketler, ASP.NET Core 5,0 ' ye dahil değildir:

* [Microsoft.Extensions.Configurlama. ](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/) [Yapılandırma sistemine](/aspnet/core/fundamentals/configuration/) [Azure Key Vault](/azure/key-vault/) tümleştiren AzureKeyVault.
* Azure Key Vault [ASP.NET Core veri koruma sistemine](/aspnet/core/security/data-protection/introduction)tümleştiren [Microsoft. Aspnetcore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/).
* [Azure Blob depolamayı](/azure/storage/blobs/) ASP.NET Core veri koruma sistemine tümleştiren [Microsoft. Aspnetcore. DataProtection. azurestorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/).

Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

#### <a name="old-behavior"></a>Eski davranış

, `Microsoft.*` Yapılandırma ve veri koruma API 'leri ile tümleştirilmiş Azure hizmetlerini paketler.

#### <a name="new-behavior"></a>Yeni davranış

Yeni `Azure.*` paketler, Azure hizmetlerini yapılandırma ve veri koruma API 'leriyle tümleştirir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, paketler şu şekilde yapılmıştır `Microsoft.*` :

* Azure SDK 'sının güncel olmayan sürümlerini kullanma. Azure SDK 'sının yeni sürümleri büyük değişiklikler yaptığından basit güncelleştirmeler yapılamıyor.
* .NET Core sürüm çizelgesine bağlıdır. Paketlerin sahipliğini Azure SDK ekibine aktarmak, Azure SDK güncelleştirildiğinde paket güncelleştirmelerinin yapılmasını sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 2,1 veya üzeri projelerde eskisini `Microsoft.*` Yeni `Azure.*` paketlerle değiştirin.

| Eskisi | Yeni |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure. Extensions. AspNetCore. DataProtection. Keys](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure. Extensions. AspNetCore. DataProtection. blob 'Lar](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.AspNetCore.Configurlama. Kaynaklanır](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

Yeni paketler Azure SDK 'sının son değişiklikleri içeren yeni bir sürümünü kullanır. Genel kullanım desenleri değiştirilmez. Bazı aşırı yüklemeler ve seçenekler, temel alınan Azure SDK API 'Lerinde değişikliklere uyum sağlamak için farklılık gösterebilir.

Eski paketler şunlardır:

* .NET Core 2,1 ve 3,1 ' nin kullanım ömrü boyunca ASP.NET Core ekibi tarafından desteklenmelidir.
* .NET 5 ' te bulunmaz.

Projenizi .NET 5 ' e yükseltirken, `Azure.*` destek sağlamak için paketlere geçiş yapın.

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
