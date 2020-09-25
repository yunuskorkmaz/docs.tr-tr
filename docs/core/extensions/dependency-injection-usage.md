---
title: .NET ' te bağımlılık ekleme 'yi kullanma
description: .NET uygulamalarınıza bağımlılık ekleme işlemini nasıl kullanacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
ms.openlocfilehash: f2298cb0be6d555a7636903dc251f022a6a62a43
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247910"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="f052e-103">Öğretici: .NET 'te bağımlılık ekleme kullanma</span><span class="sxs-lookup"><span data-stu-id="f052e-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="f052e-104">Bu öğreticide [, .net 'te bağımlılık ekleme (dı)](dependency-injection.md)'nin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f052e-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="f052e-105">*Microsoft uzantıları*ile,, hizmetlerin bir içinde eklendiği ve yapılandırıldığı birinci sınıf bir vatandaşlık <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="f052e-105">With *Microsoft Extensions*, DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="f052e-106"><xref:Microsoft.Extensions.Hosting.IHost>Arabirim, <xref:System.IServiceProvider> Tüm kayıtlı hizmetlerin kapsayıcısı olarak davranan örneği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="f052e-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="f052e-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f052e-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f052e-108">Bağımlılık ekleme 'yi kullanan bir .NET konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f052e-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="f052e-109">[Genel bir konak](generic-host.md) oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f052e-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="f052e-110">Çeşitli arabirimler ve ilgili uygulamalar yazın</span><span class="sxs-lookup"><span data-stu-id="f052e-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="f052e-111">Dı için hizmet ömrünü ve kapsamını kullanma</span><span class="sxs-lookup"><span data-stu-id="f052e-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f052e-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f052e-112">Prerequisites</span></span>

- <span data-ttu-id="f052e-113">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="f052e-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="f052e-114">Tümleşik bir geliştirme ortamı (IDE), [Visual Studio, Visual Studio Code veya Mac için Visual Studio](https://visualstudio.microsoft.com) tüm geçerli seçimlerdir.</span><span class="sxs-lookup"><span data-stu-id="f052e-114">An Integrated Development Environment (IDE), [Visual Studio, Visual Studio Code, or Visual Studio for Mac](https://visualstudio.microsoft.com) are all valid choices.</span></span>
- <span data-ttu-id="f052e-115">Yeni .NET uygulamaları oluşturma ve NuGet paketleri yükleme hakkında benzerlik.</span><span class="sxs-lookup"><span data-stu-id="f052e-115">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="f052e-116">Yeni bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f052e-116">Create a new console application</span></span>

<span data-ttu-id="f052e-117">[DotNet New](../tools/dotnet-new.md) komutunu ya da IDE yeni proje sihirbazını kullanarak **Consoledi. example**adlı yeni bir .NET konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f052e-117">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example**.</span></span> <span data-ttu-id="f052e-118">Projeye [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f052e-118">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="f052e-119">Arabirim Ekle</span><span class="sxs-lookup"><span data-stu-id="f052e-119">Add interfaces</span></span>

<span data-ttu-id="f052e-120">Aşağıdaki arayüzleri proje kök dizinine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f052e-120">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="f052e-121">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="f052e-121">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="f052e-122">`IOperation`Arabirim tek bir özelliği tanımlar `OperationId` .</span><span class="sxs-lookup"><span data-stu-id="f052e-122">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="f052e-123">*ITransientOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="f052e-123">*ITransientOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

<span data-ttu-id="f052e-124">*IScopedOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="f052e-124">*IScopedOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

<span data-ttu-id="f052e-125">*ISingletonOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="f052e-125">*ISingletonOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

<span data-ttu-id="f052e-126">Tüm alt arabirimlerin `IOperation` amaçlanan hizmet ömrünü adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f052e-126">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="f052e-127">Örneğin, "geçici" veya "tek".</span><span class="sxs-lookup"><span data-stu-id="f052e-127">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="f052e-128">Varsayılan uygulama ekle</span><span class="sxs-lookup"><span data-stu-id="f052e-128">Add default implementation</span></span>

<span data-ttu-id="f052e-129">Çeşitli işlemler için aşağıdaki varsayılan uygulamayı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f052e-129">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="f052e-130">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="f052e-130">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="f052e-131">, `DefaultOperation` Tüm adlandırılmış/işaret arabirimlerini uygular ve `OperationId` Yeni bir genel benzersiz TANıMLAYıCıNıN (GUID) son dört karakterine özelliği başlatır.</span><span class="sxs-lookup"><span data-stu-id="f052e-131">The `DefaultOperation` implements all of the named/marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="f052e-132">DI gerektiren hizmet ekleyin</span><span class="sxs-lookup"><span data-stu-id="f052e-132">Add service that requires DI</span></span>

<span data-ttu-id="f052e-133">Konsol uygulamanıza hizmet olarak davranan aşağıdaki işlem günlükçüsü nesnesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f052e-133">Add the following operation logger object, which acts as a service to your console application:</span></span>

<span data-ttu-id="f052e-134">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="f052e-134">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="f052e-135">,, Ve ' nin `OperationLogger` her birini gerektiren bir oluşturucu tanımlar, yani, `ITransientOperation` `IScopedOperation` ve `ISingletonOperation` .</span><span class="sxs-lookup"><span data-stu-id="f052e-135">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="f052e-136">Nesnesi, tüketicinin belirli bir parametreyle işlemleri günlüğe açmasını sağlayan tek bir yöntem sunar `scope` .</span><span class="sxs-lookup"><span data-stu-id="f052e-136">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="f052e-137">Çağrıldığında, `LogOperations` yöntemi her bir işlemin benzersiz tanımlayıcısını kapsam dizesi ve iletisiyle günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f052e-137">When invoked, the `LogOperations` method will log each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="f052e-138">Dı için Hizmetleri Kaydet</span><span class="sxs-lookup"><span data-stu-id="f052e-138">Register services for DI</span></span>

<span data-ttu-id="f052e-139">Son olarak, *program.cs* dosyasını aşağıda eşleşecek şekilde güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="f052e-139">Finally, update the *Program.cs* file to match following:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="f052e-140">Uygulama:</span><span class="sxs-lookup"><span data-stu-id="f052e-140">The application:</span></span>

- <span data-ttu-id="f052e-141"><xref:Microsoft.Extensions.Hosting.IHostBuilder> [Varsayılan bağlayıcı ayarlarına](generic-host.md#default-builder-settings)sahip bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f052e-141">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="f052e-142">Hizmetleri yapılandırır ve bunlara karşılık gelen hizmet ömrüne ekler.</span><span class="sxs-lookup"><span data-stu-id="f052e-142">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="f052e-143"><xref:Microsoft.Extensions.Hosting.IHostBuilder.Build>Bir örneğini çağırır ve atar <xref:Microsoft.Extensions.Hosting.IHost> .</span><span class="sxs-lookup"><span data-stu-id="f052e-143">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="f052e-144">Çağrılar `ExemplifyScoping` , öğesini geçirme <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f052e-144">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="f052e-145">Sonuç</span><span class="sxs-lookup"><span data-stu-id="f052e-145">Conclusion</span></span>

<span data-ttu-id="f052e-146">Uygulama, aşağıdaki örneğe benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="f052e-146">The application produces output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

<span data-ttu-id="f052e-147">Uygulama çıktısından aşağıdakileri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f052e-147">From the application output, you can see that:</span></span>

- <span data-ttu-id="f052e-148">Geçici işlemler her zaman farklıdır, yani hizmetin her alımı ile yeni bir örnek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f052e-148">Transient operations are always different, meaning a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="f052e-149">Kapsamlı işlemler yalnızca yeni bir kapsamla değiştirilir, ancak bir kapsam içinde aynı örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f052e-149">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="f052e-150">Tek işlemler her zaman aynıdır, yani yeni bir örnek yalnızca bir kez oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f052e-150">Singleton operations are always the same, meaning a new instance is only created once.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f052e-151">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f052e-151">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f052e-152">Bağımlılık ekleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f052e-152">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
