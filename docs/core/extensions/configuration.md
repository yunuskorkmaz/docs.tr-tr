---
title: .NET 'teki yapılandırma
description: .NET uygulamalarını yapılandırmak için yapılandırma API 'sini kullanmayı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: overview
ms.openlocfilehash: f97bd3fd4881c6b0939635ec2372aee21c670d5d
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720811"
---
# <a name="configuration-in-net"></a>.NET 'teki yapılandırma

.NET 'teki yapılandırma bir veya daha fazla [yapılandırma sağlayıcısı](#configuration-providers)kullanılarak gerçekleştirilir. Yapılandırma sağlayıcıları çeşitli yapılandırma kaynakları kullanarak anahtar-değer çiftlerinden yapılandırma verilerini okur:

- *appsettings.js* gibi ayarlar dosyaları
- Ortam değişkenleri
- [Azure Key Vault](/azure/key-vault/general/overview)
- [Azure Uygulama Yapılandırması](/azure/azure-app-configuration/overview)
- Komut satırı bağımsız değişkenleri
- Özel sağlayıcılar, yüklendi veya oluşturuldu
- Dizin dosyaları
- Bellek içi .NET nesneleri

## <a name="configure-console-apps"></a>Konsol uygulamalarını yapılandırma

Varsayılan olarak [DotNet New](../tools/dotnet-new.md) veya Visual Studio kullanılarak oluşturulan yeni .NET konsol uygulamaları yapılandırma *yeteneklerini sunmaz.* Yeni bir .NET konsol uygulamasına yapılandırma eklemek için, öğesine [bir paket başvurusu ekleyin](../tools/dotnet-add-package.md) `Microsoft.Extensions.Hosting` . *Program.cs* dosyasını aşağıdaki kodla eşleşecek şekilde değiştirin:

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

<xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType>Yöntemi, uygulama için aşağıdaki sırayla varsayılan yapılandırma sağlar:

1. [Chainedconfigurationprovider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource) : var olan bir `IConfiguration` kaynak olarak ekler.
1. [JSON yapılandırma sağlayıcısını](configuration-providers.md#file-configuration-provider)kullanarak *appsettings.js* .
1. *appSettings.* `Environment` [JSON yapılandırma sağlayıcısı](configuration-providers.md#file-configuration-provider)kullanılarak *. JSON* . Örneğin, *appSettings*. ***Üretim***. *JSON* ve *appSettings*. ***Geliştirme***. *JSON*.
1. Uygulama ortamda çalıştırıldığında uygulama gizli dizileri `Development` .
1. Ortam [değişkenleri yapılandırma sağlayıcısını](configuration-providers.md#environment-variable-configuration-provider)kullanarak ortam değişkenleri.
1. Komut satırı [yapılandırma sağlayıcısını](configuration-providers.md#command-line-configuration-provider)kullanan komut satırı bağımsız değişkenleri.

Daha sonra eklenen yapılandırma sağlayıcıları önceki anahtar ayarlarını geçersiz kılar. Örneğin, `SomeKey` ve ortamında hem *appsettings.js* hem de ortamda ayarlandıysa, ortam değeri kullanılır. Varsayılan yapılandırma sağlayıcılarını kullanarak, [komut satırı yapılandırma sağlayıcısı](configuration-providers.md#command-line-configuration-provider) diğer tüm sağlayıcıları geçersiz kılar.

### <a name="binding"></a>Bağlama

.NET 'teki yapılandırmaya yönelik temel avantajlardan biri, yapılandırma değerlerini .NET nesnelerinin örneklerine bağlama olanağıdır. Örneğin, JSON yapılandırma sağlayıcısı dosyalardaki *appsettings.js* .NET nesneleriyle eşlemek için kullanılabilir ve bağımlılık ekleme ile kullanılır. Bu seçenek, Seçenekler deseninin, ilgili ayarlar gruplarına kesin olarak belirlenmiş erişim sağlamak için sınıfları kullanır.

## <a name="configuration-providers"></a>Yapılandırma sağlayıcıları

Aşağıdaki tabloda .NET Core uygulamaları için kullanılabilen yapılandırma sağlayıcıları gösterilmektedir.

| Sağlayıcı                                                                                                               | Şuradan yapılandırma sağlar        |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [Azure uygulama yapılandırma sağlayıcısı](/azure/azure-app-configuration/quickstart-aspnet-core-app)                          | Azure Uygulama Yapılandırması            |
| [Azure Key Vault yapılandırma sağlayıcısı](/azure/key-vault/general/tutorial-net-virtual-machine)                        | Azure Key Vault                    |
| [Komut satırı yapılandırma sağlayıcısı](configuration-providers.md#command-line-configuration-provider)                  | Komut satırı parametreleri            |
| [Özel yapılandırma sağlayıcısı](custom-configuration-provider.md)                                                      | Özel kaynak                      |
| [Ortam değişkenleri yapılandırma sağlayıcısı](configuration-providers.md#environment-variable-configuration-provider) | Ortam değişkenleri              |
| [Dosya yapılandırma sağlayıcısı](configuration-providers.md#file-configuration-provider)                                  | JSON, XML ve ıNı dosyaları           |
| [Dosya başına anahtar yapılandırma sağlayıcısı](configuration-providers.md#key-per-file-configuration-provider)                  | Dizin dosyaları                    |
| [Bellek yapılandırma sağlayıcısı](configuration-providers.md#memory-configuration-provider)                              | Bellek içi Koleksiyonlar              |
| [Uygulama gizli dizileri (gizli yönetici)](/aspnet/core/security/app-secrets)                                                      | Kullanıcı profili dizinindeki dosya |

Çeşitli yapılandırma sağlayıcıları hakkında daha fazla bilgi için bkz. [.net 'Teki yapılandırma sağlayıcıları](configuration-providers.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'teki yapılandırma sağlayıcıları](configuration-providers.md)
- [Özel bir yapılandırma sağlayıcısı uygulama](custom-configuration-provider.md)
