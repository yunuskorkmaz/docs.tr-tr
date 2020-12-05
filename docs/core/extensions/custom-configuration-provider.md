---
title: .NET ' te özel bir yapılandırma sağlayıcısı uygulama
description: .NET uygulamalarında özel bir yapılandırma sağlayıcısı uygulamayı nasıl uygulayacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.topic: how-to
ms.openlocfilehash: 22e46b7df8b02421633d6be251d990879baa8b2b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740119"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a><span data-ttu-id="52643-103">.NET ' te özel bir yapılandırma sağlayıcısı uygulama</span><span class="sxs-lookup"><span data-stu-id="52643-103">Implement a custom configuration provider in .NET</span></span>

<span data-ttu-id="52643-104">JSON, XML ve ıNı dosyaları gibi yaygın yapılandırma kaynakları için kullanılabilen birçok [yapılandırma sağlayıcısı](configuration-providers.md) vardır.</span><span class="sxs-lookup"><span data-stu-id="52643-104">There are many [configuration providers](configuration-providers.md) available for common configuration sources such as JSON, XML, and INI files.</span></span> <span data-ttu-id="52643-105">Kullanılabilir sağlayıcılardan biri uygulama gereksinimlerinize uygun olmadığında özel bir yapılandırma sağlayıcısı uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="52643-105">You may need to implement a custom configuration provider when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="52643-106">Bu makalede, yapılandırma kaynağı olarak bir veritabanını temel alan özel bir yapılandırma sağlayıcısını nasıl uygulayacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="52643-106">In this article, you'll learn how to implement a custom configuration provider that relies on a database as its configuration source.</span></span>

## <a name="custom-configuration-provider"></a><span data-ttu-id="52643-107">Özel yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="52643-107">Custom configuration provider</span></span>

<span data-ttu-id="52643-108">Örnek uygulama, [Entity Framework (EF) Core](/ef/core)kullanarak bir veritabanından yapılandırma anahtar-değer çiftlerini okuyan temel bir yapılandırma sağlayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="52643-108">The sample app demonstrates how to create a basic configuration provider that reads configuration key-value pairs from a database using [Entity Framework (EF) Core](/ef/core).</span></span>

<span data-ttu-id="52643-109">Sağlayıcı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="52643-109">The provider has the following characteristics:</span></span>

- <span data-ttu-id="52643-110">EF bellek içi veritabanı, tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52643-110">The EF in-memory database is used for demonstration purposes.</span></span> <span data-ttu-id="52643-111">Bağlantı dizesi gerektiren bir veritabanını kullanmak için, `ConfigurationBuilder` başka bir yapılandırma sağlayıcısından bağlantı dizesini sağlamak üzere bir ikincil uygulayın.</span><span class="sxs-lookup"><span data-stu-id="52643-111">To use a database that requires a connection string, implement a secondary `ConfigurationBuilder` to supply the connection string from another configuration provider.</span></span>
- <span data-ttu-id="52643-112">Sağlayıcı bir veritabanı tablosunu başlangıçta yapılandırmaya okur.</span><span class="sxs-lookup"><span data-stu-id="52643-112">The provider reads a database table into configuration at startup.</span></span> <span data-ttu-id="52643-113">Sağlayıcı, her anahtar temelinde veritabanını sorgulayamaz.</span><span class="sxs-lookup"><span data-stu-id="52643-113">The provider doesn't query the database on a per-key basis.</span></span>
- <span data-ttu-id="52643-114">Değişiklik değişikliği uygulanmadı, bu nedenle uygulama başladıktan sonra veritabanının güncelleştirilmesi uygulamanın yapılandırması üzerinde hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="52643-114">Reload-on-change isn't implemented, so updating the database after the app starts has no effect on the app's configuration.</span></span>

<span data-ttu-id="52643-115">`Settings`Yapılandırma değerlerini veritabanında depolamak için bir kayıt türü varlığı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52643-115">Define a `Settings` record type entity for storing configuration values in the database.</span></span> <span data-ttu-id="52643-116">Örneğin, *modeller* klasörünüze bir *Settings.cs* dosyası ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52643-116">For example, you could add a *Settings.cs* file in your *Models* folder:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

<span data-ttu-id="52643-117">Kayıt türleri hakkında bilgi için bkz. [C# 9 ' da kayıt türleri](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="52643-117">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="52643-118">Bir `EntityConfigurationContext` mağazaya ekleyin ve yapılandırılan değerlere erişin.</span><span class="sxs-lookup"><span data-stu-id="52643-118">Add an `EntityConfigurationContext` to store and access the configured values.</span></span>

<span data-ttu-id="52643-119">*Sağlayıcılar/EntityConfigurationContext. cs*:</span><span class="sxs-lookup"><span data-stu-id="52643-119">*Providers/EntityConfigurationContext.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<span data-ttu-id="52643-120">Uygulayan bir sınıf oluşturun <xref:Microsoft.Extensions.Configuration.IConfigurationSource> .</span><span class="sxs-lookup"><span data-stu-id="52643-120">Create a class that implements <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span></span>

<span data-ttu-id="52643-121">*Sağlayıcılar/EntityConfigurationSource. cs*:</span><span class="sxs-lookup"><span data-stu-id="52643-121">*Providers/EntityConfigurationSource.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<span data-ttu-id="52643-122">Öğesinden devralarak özel yapılandırma sağlayıcısını oluşturun <xref:Microsoft.Extensions.Configuration.ConfigurationProvider> .</span><span class="sxs-lookup"><span data-stu-id="52643-122">Create the custom configuration provider by inheriting from <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span></span> <span data-ttu-id="52643-123">Yapılandırma sağlayıcısı boş olduğunda veritabanını başlatır.</span><span class="sxs-lookup"><span data-stu-id="52643-123">The configuration provider initializes the database when it's empty.</span></span> <span data-ttu-id="52643-124">Yapılandırma anahtarları büyük/küçük harfe duyarsız olduğundan, veritabanını başlatmak için kullanılan sözlük, büyük/küçük harf duyarsız karşılaştırıcı ([StringComparer. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)) ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="52643-124">Since configuration keys are case-insensitive, the dictionary used to initialize the database is created with the case-insensitive comparer ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span></span>

<span data-ttu-id="52643-125">*Sağlayıcılar/EntityConfigurationProvider. cs*:</span><span class="sxs-lookup"><span data-stu-id="52643-125">*Providers/EntityConfigurationProvider.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

<span data-ttu-id="52643-126">`AddEntityConfiguration`Genişletme yöntemi, yapılandırma kaynağının bir örneğe eklenmesine izin verir <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> .</span><span class="sxs-lookup"><span data-stu-id="52643-126">An `AddEntityConfiguration` extension method permits adding the configuration source to a <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span></span>

<span data-ttu-id="52643-127">*Extensions/ConfigurationBuilderExtensions. cs*:</span><span class="sxs-lookup"><span data-stu-id="52643-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

<span data-ttu-id="52643-128">Aşağıdaki kod, `EntityConfigurationProvider` *program.cs* içinde özel kullanımı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="52643-128">The following code shows how to use the custom `EntityConfigurationProvider` in *Program.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="27-28":::

## <a name="see-also"></a><span data-ttu-id="52643-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52643-129">See also</span></span>

- [<span data-ttu-id="52643-130">.NET 'teki yapılandırma</span><span class="sxs-lookup"><span data-stu-id="52643-130">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="52643-131">.NET 'teki yapılandırma sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="52643-131">Configuration providers in .NET</span></span>](configuration-providers.md)
