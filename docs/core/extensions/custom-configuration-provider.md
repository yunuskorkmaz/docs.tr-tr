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
# <a name="implement-a-custom-configuration-provider-in-net"></a><span data-ttu-id="c06c9-103">.NET ' te özel bir yapılandırma sağlayıcısı uygulama</span><span class="sxs-lookup"><span data-stu-id="c06c9-103">Implement a custom configuration provider in .NET</span></span>

<span data-ttu-id="c06c9-104">JSON, XML ve ıNı dosyaları gibi yaygın yapılandırma kaynakları için kullanılabilen birçok [yapılandırma sağlayıcısı](configuration-providers.md) vardır.</span><span class="sxs-lookup"><span data-stu-id="c06c9-104">There are many [configuration providers](configuration-providers.md) available for common configuration sources such as JSON, XML, and INI files.</span></span> <span data-ttu-id="c06c9-105">Kullanılabilir sağlayıcılardan biri uygulama gereksinimlerinize uygun olmadığında özel bir yapılandırma sağlayıcısı uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c06c9-105">You may need to implement a custom configuration provider when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="c06c9-106">Bu makalede, yapılandırma kaynağı olarak bir veritabanını temel alan özel bir yapılandırma sağlayıcısını nasıl uygulayacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c06c9-106">In this article, you'll learn how to implement a custom configuration provider that relies on a database as its configuration source.</span></span>

## <a name="custom-configuration-provider"></a><span data-ttu-id="c06c9-107">Özel yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c06c9-107">Custom configuration provider</span></span>

<span data-ttu-id="c06c9-108">Örnek uygulama, [Entity Framework (EF) Core](/ef/core)kullanarak bir veritabanından yapılandırma anahtar-değer çiftlerini okuyan temel bir yapılandırma sağlayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c06c9-108">The sample app demonstrates how to create a basic configuration provider that reads configuration key-value pairs from a database using [Entity Framework (EF) Core](/ef/core).</span></span>

<span data-ttu-id="c06c9-109">Sağlayıcı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c06c9-109">The provider has the following characteristics:</span></span>

- <span data-ttu-id="c06c9-110">EF bellek içi veritabanı, tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c06c9-110">The EF in-memory database is used for demonstration purposes.</span></span> <span data-ttu-id="c06c9-111">Bağlantı dizesi gerektiren bir veritabanını kullanmak için, `ConfigurationBuilder` başka bir yapılandırma sağlayıcısından bağlantı dizesini sağlamak üzere bir ikincil uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c06c9-111">To use a database that requires a connection string, implement a secondary `ConfigurationBuilder` to supply the connection string from another configuration provider.</span></span>
- <span data-ttu-id="c06c9-112">Sağlayıcı bir veritabanı tablosunu başlangıçta yapılandırmaya okur.</span><span class="sxs-lookup"><span data-stu-id="c06c9-112">The provider reads a database table into configuration at startup.</span></span> <span data-ttu-id="c06c9-113">Sağlayıcı, her anahtar temelinde veritabanını sorgulayamaz.</span><span class="sxs-lookup"><span data-stu-id="c06c9-113">The provider doesn't query the database on a per-key basis.</span></span>
- <span data-ttu-id="c06c9-114">Değişiklik değişikliği uygulanmadı, bu nedenle uygulama başladıktan sonra veritabanının güncelleştirilmesi uygulamanın yapılandırması üzerinde hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="c06c9-114">Reload-on-change isn't implemented, so updating the database after the app starts has no effect on the app's configuration.</span></span>

<span data-ttu-id="c06c9-115">`Settings`Yapılandırma değerlerini veritabanında depolamak için bir kayıt türü varlığı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c06c9-115">Define a `Settings` record type entity for storing configuration values in the database.</span></span> <span data-ttu-id="c06c9-116">Örneğin, *modeller* klasörünüze bir *Settings.cs* dosyası ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c06c9-116">For example, you could add a *Settings.cs* file in your *Models* folder:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

<span data-ttu-id="c06c9-117">Kayıt türleri hakkında bilgi için bkz. [C# 9 ' da kayıt türleri](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="c06c9-117">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="c06c9-118">Bir `EntityConfigurationContext` mağazaya ekleyin ve yapılandırılan değerlere erişin.</span><span class="sxs-lookup"><span data-stu-id="c06c9-118">Add an `EntityConfigurationContext` to store and access the configured values.</span></span>

<span data-ttu-id="c06c9-119">*Sağlayıcılar/EntityConfigurationContext. cs*:</span><span class="sxs-lookup"><span data-stu-id="c06c9-119">*Providers/EntityConfigurationContext.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<span data-ttu-id="c06c9-120">Uygulayan bir sınıf oluşturun <xref:Microsoft.Extensions.Configuration.IConfigurationSource> .</span><span class="sxs-lookup"><span data-stu-id="c06c9-120">Create a class that implements <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span></span>

<span data-ttu-id="c06c9-121">*Sağlayıcılar/EntityConfigurationSource. cs*:</span><span class="sxs-lookup"><span data-stu-id="c06c9-121">*Providers/EntityConfigurationSource.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<span data-ttu-id="c06c9-122">Öğesinden devralarak özel yapılandırma sağlayıcısını oluşturun <xref:Microsoft.Extensions.Configuration.ConfigurationProvider> .</span><span class="sxs-lookup"><span data-stu-id="c06c9-122">Create the custom configuration provider by inheriting from <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span></span> <span data-ttu-id="c06c9-123">Yapılandırma sağlayıcısı boş olduğunda veritabanını başlatır.</span><span class="sxs-lookup"><span data-stu-id="c06c9-123">The configuration provider initializes the database when it's empty.</span></span> <span data-ttu-id="c06c9-124">Yapılandırma anahtarları büyük/küçük harfe duyarsız olduğundan, veritabanını başlatmak için kullanılan sözlük, büyük/küçük harf duyarsız karşılaştırıcı ([StringComparer. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)) ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c06c9-124">Since configuration keys are case-insensitive, the dictionary used to initialize the database is created with the case-insensitive comparer ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span></span>

<span data-ttu-id="c06c9-125">*Sağlayıcılar/EntityConfigurationProvider. cs*:</span><span class="sxs-lookup"><span data-stu-id="c06c9-125">*Providers/EntityConfigurationProvider.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

<span data-ttu-id="c06c9-126">`AddEntityConfiguration`Genişletme yöntemi, yapılandırma kaynağının bir örneğe eklenmesine izin verir <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> .</span><span class="sxs-lookup"><span data-stu-id="c06c9-126">An `AddEntityConfiguration` extension method permits adding the configuration source to a <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span></span>

<span data-ttu-id="c06c9-127">*Extensions/ConfigurationBuilderExtensions. cs*:</span><span class="sxs-lookup"><span data-stu-id="c06c9-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

<span data-ttu-id="c06c9-128">Aşağıdaki kod, `EntityConfigurationProvider` *program.cs*içinde özel kullanımı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c06c9-128">The following code shows how to use the custom `EntityConfigurationProvider` in *Program.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="21-22":::

## <a name="see-also"></a><span data-ttu-id="c06c9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c06c9-129">See also</span></span>

- [<span data-ttu-id="c06c9-130">.NET 'teki yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c06c9-130">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="c06c9-131">.NET 'teki yapılandırma sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c06c9-131">Configuration providers in .NET</span></span>](configuration-providers.md)
