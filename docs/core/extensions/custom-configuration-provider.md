---
title: .NET ' te özel bir yapılandırma sağlayıcısı uygulama
description: .NET uygulamalarında özel bir yapılandırma sağlayıcısı uygulamayı nasıl uygulayacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: how-to
ms.openlocfilehash: 968bf202eeea32742444681260d5ab0b27b403f9
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720810"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a>.NET ' te özel bir yapılandırma sağlayıcısı uygulama

JSON, XML ve ıNı dosyaları gibi yaygın yapılandırma kaynakları için kullanılabilen birçok [yapılandırma sağlayıcısı](configuration-providers.md) vardır. Kullanılabilir sağlayıcılardan biri uygulama gereksinimlerinize uygun olmadığında özel bir yapılandırma sağlayıcısı uygulamanız gerekebilir. Bu makalede, yapılandırma kaynağı olarak bir veritabanını temel alan özel bir yapılandırma sağlayıcısını nasıl uygulayacağınızı öğreneceksiniz.

## <a name="custom-configuration-provider"></a>Özel yapılandırma sağlayıcısı

Örnek uygulama, [Entity Framework (EF) Core](/ef/core)kullanarak bir veritabanından yapılandırma anahtar-değer çiftlerini okuyan temel bir yapılandırma sağlayıcısı oluşturmayı gösterir.

Sağlayıcı aşağıdaki özelliklere sahiptir:

- EF bellek içi veritabanı, tanıtım amacıyla kullanılır. Bağlantı dizesi gerektiren bir veritabanını kullanmak için, `ConfigurationBuilder` başka bir yapılandırma sağlayıcısından bağlantı dizesini sağlamak üzere bir ikincil uygulayın.
- Sağlayıcı bir veritabanı tablosunu başlangıçta yapılandırmaya okur. Sağlayıcı, her anahtar temelinde veritabanını sorgulayamaz.
- Değişiklik değişikliği uygulanmadı, bu nedenle uygulama başladıktan sonra veritabanının güncelleştirilmesi uygulamanın yapılandırması üzerinde hiçbir etkiye sahip değildir.

`Settings`Yapılandırma değerlerini veritabanında depolamak için bir kayıt türü varlığı tanımlayın. Örneğin, *modeller* klasörünüze bir *Settings.cs* dosyası ekleyebilirsiniz:

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

Kayıt türleri hakkında bilgi için bkz. [C# 9 ' da kayıt türleri](../../csharp/whats-new/csharp-9.md#record-types).

Bir `EntityConfigurationContext` mağazaya ekleyin ve yapılandırılan değerlere erişin.

*Sağlayıcılar/EntityConfigurationContext. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

Uygulayan bir sınıf oluşturun <xref:Microsoft.Extensions.Configuration.IConfigurationSource> .

*Sağlayıcılar/EntityConfigurationSource. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

Öğesinden devralarak özel yapılandırma sağlayıcısını oluşturun <xref:Microsoft.Extensions.Configuration.ConfigurationProvider> . Yapılandırma sağlayıcısı boş olduğunda veritabanını başlatır. Yapılandırma anahtarları büyük/küçük harfe duyarsız olduğundan, veritabanını başlatmak için kullanılan sözlük, büyük/küçük harf duyarsız karşılaştırıcı ([StringComparer. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)) ile oluşturulur.

*Sağlayıcılar/EntityConfigurationProvider. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

`AddEntityConfiguration`Genişletme yöntemi, yapılandırma kaynağının bir örneğe eklenmesine izin verir <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> .

*Extensions/ConfigurationBuilderExtensions. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

Aşağıdaki kod, `EntityConfigurationProvider` *program.cs*içinde özel kullanımı göstermektedir:

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="21-22":::

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'teki yapılandırma](configuration.md)
- [.NET 'teki yapılandırma sağlayıcıları](configuration-providers.md)
