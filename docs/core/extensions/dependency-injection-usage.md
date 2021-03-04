---
title: .NET ' te bağımlılık ekleme 'yi kullanma
description: .NET uygulamalarınıza bağımlılık ekleme işlemini nasıl kullanacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 11/13/2020
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: d6654d5d1c8f7959e96998c18a1790cce46ebf41
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105564"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="c8b92-103">Öğretici: .NET 'te bağımlılık ekleme kullanma</span><span class="sxs-lookup"><span data-stu-id="c8b92-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="c8b92-104">Bu öğreticide [, .net 'te bağımlılık ekleme (dı)](dependency-injection.md)'nin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8b92-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="c8b92-105">*Microsoft uzantıları* ile,, hizmetlerin bir içinde eklendiği ve yapılandırıldığı birinci sınıf bir vatandaşlık <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="c8b92-105">With *Microsoft Extensions*, DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="c8b92-106"><xref:Microsoft.Extensions.Hosting.IHost>Arabirim, <xref:System.IServiceProvider> Tüm kayıtlı hizmetlerin kapsayıcısı olarak davranan örneği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c8b92-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="c8b92-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c8b92-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c8b92-108">Bağımlılık ekleme 'yi kullanan bir .NET konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8b92-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="c8b92-109">[Genel bir konak](generic-host.md) oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c8b92-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="c8b92-110">Çeşitli arabirimler ve ilgili uygulamalar yazın</span><span class="sxs-lookup"><span data-stu-id="c8b92-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="c8b92-111">Dı için hizmet ömrünü ve kapsamını kullanma</span><span class="sxs-lookup"><span data-stu-id="c8b92-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8b92-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c8b92-112">Prerequisites</span></span>

- <span data-ttu-id="c8b92-113">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet) veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c8b92-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or later.</span></span>
- <span data-ttu-id="c8b92-114">Yeni .NET uygulamaları oluşturma ve NuGet paketleri yükleme hakkında benzerlik.</span><span class="sxs-lookup"><span data-stu-id="c8b92-114">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="c8b92-115">Yeni bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8b92-115">Create a new console application</span></span>

<span data-ttu-id="c8b92-116">[DotNet New](../tools/dotnet-new.md) komutunu ya da IDE yeni proje sihirbazını kullanarak **Example consoledi** adlı yeni bir .NET konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8b92-116">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example**.</span></span> <span data-ttu-id="c8b92-117">Projeye [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8b92-117">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="c8b92-118">Arabirim Ekle</span><span class="sxs-lookup"><span data-stu-id="c8b92-118">Add interfaces</span></span>

<span data-ttu-id="c8b92-119">Aşağıdaki arayüzleri proje kök dizinine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c8b92-119">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="c8b92-120">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="c8b92-120">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="c8b92-121">`IOperation`Arabirim tek bir özelliği tanımlar `OperationId` .</span><span class="sxs-lookup"><span data-stu-id="c8b92-121">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="c8b92-122">*I Transient Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="c8b92-122">*ITransientOperation.cs*</span></span>

<span data-ttu-id="c8b92-123">::: Code Language = "CSharp" Source = "parçacıklar/Configuration/Console-dı/ı Transient Operation.cs":::</span><span class="sxs-lookup"><span data-stu-id="c8b92-123">:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::</span></span>

<span data-ttu-id="c8b92-124">*I Scoped Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="c8b92-124">*IScopedOperation.cs*</span></span>

<span data-ttu-id="c8b92-125">::: Code Language = "CSharp" Source = "parçacıklar/Configuration/Console-dı/ı Scoped Operation.cs":::</span><span class="sxs-lookup"><span data-stu-id="c8b92-125">:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::</span></span>

<span data-ttu-id="c8b92-126">*I Singleton Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="c8b92-126">*ISingletonOperation.cs*</span></span>

<span data-ttu-id="c8b92-127">::: Code Language = "CSharp" Source = "parçacıklar/Configuration/Console-dı/ı Singleton Operation.cs":::</span><span class="sxs-lookup"><span data-stu-id="c8b92-127">:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::</span></span>

<span data-ttu-id="c8b92-128">Tüm alt arabirimlerin `IOperation` amaçlanan hizmet ömrünü adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c8b92-128">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="c8b92-129">Örneğin, " Transient " veya " Singleton ".</span><span class="sxs-lookup"><span data-stu-id="c8b92-129">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="c8b92-130">Varsayılan uygulama ekle</span><span class="sxs-lookup"><span data-stu-id="c8b92-130">Add default implementation</span></span>

<span data-ttu-id="c8b92-131">Çeşitli işlemler için aşağıdaki varsayılan uygulamayı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c8b92-131">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="c8b92-132">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="c8b92-132">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="c8b92-133">, `DefaultOperation` Tüm adlandırılmış işaret arabirimlerini uygular ve `OperationId` Yeni bir genel benzersiz TANıMLAYıCıNıN (GUID) son dört karakterine özelliği başlatır.</span><span class="sxs-lookup"><span data-stu-id="c8b92-133">The `DefaultOperation` implements all of the named marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="c8b92-134">DI gerektiren hizmet ekleyin</span><span class="sxs-lookup"><span data-stu-id="c8b92-134">Add service that requires DI</span></span>

<span data-ttu-id="c8b92-135">Konsol uygulamasına bir hizmet olarak davranan aşağıdaki işlem günlükçüsü nesnesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c8b92-135">Add the following operation logger object, which acts as a service to the console app:</span></span>

<span data-ttu-id="c8b92-136">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="c8b92-136">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="c8b92-137">,, Ve ' nin `OperationLogger` her birini gerektiren bir oluşturucu tanımlar, yani, `ITransientOperation` `IScopedOperation` ve `ISingletonOperation` .</span><span class="sxs-lookup"><span data-stu-id="c8b92-137">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="c8b92-138">Nesnesi, tüketicinin belirli bir parametreyle işlemleri günlüğe açmasını sağlayan tek bir yöntem sunar `scope` .</span><span class="sxs-lookup"><span data-stu-id="c8b92-138">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="c8b92-139">Çağrıldığında, `LogOperations` yöntemi her bir işlemin benzersiz tanımlayıcısını kapsam dizesi ve iletisiyle günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c8b92-139">When invoked, the `LogOperations` method logs each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="c8b92-140">Dı için Hizmetleri Kaydet</span><span class="sxs-lookup"><span data-stu-id="c8b92-140">Register services for DI</span></span>

<span data-ttu-id="c8b92-141">Aşağıdaki kodla *program.cs* güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="c8b92-141">Update *Program.cs* with the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

> <span data-ttu-id="c8b92-142">Her `services.Add{SERVICE_NAME}` genişletme yöntemi, hizmetlerini ekler ve potansiyel olarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c8b92-142">Each `services.Add{SERVICE_NAME}` extension method adds, and potentially configures, services.</span></span> <span data-ttu-id="c8b92-143">Uygulamaların bu kuralı izlemesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="c8b92-143">We recommended that apps follow this convention.</span></span> <span data-ttu-id="c8b92-144"><xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName>Hizmet kaydı gruplarını kapsüllemek için uzantı yöntemlerini ad alanına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c8b92-144">Place extension methods in the <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName> namespace to encapsulate groups of service registrations.</span></span> <span data-ttu-id="c8b92-145">Dı uzantısı yöntemlerine ilişkin ad alanı bölümü de dahil olmak üzere `Microsoft.Extensions.DependencyInjection` :</span><span class="sxs-lookup"><span data-stu-id="c8b92-145">Including the namespace portion `Microsoft.Extensions.DependencyInjection` for DI extension methods also:</span></span>
>
> - <span data-ttu-id="c8b92-146">Ek blokları eklemeden [IntelliSense](/visualstudio/ide/using-intellisense) 'de görüntülenmesine izin verir `using` .</span><span class="sxs-lookup"><span data-stu-id="c8b92-146">Allows them to be displayed in [IntelliSense](/visualstudio/ide/using-intellisense) without adding additional `using` blocks.</span></span>
> - <span data-ttu-id="c8b92-147">`using` `Program` `Startup` Bu uzantı yöntemlerinin genellikle çağrıldığı, veya sınıflarında aşırı deyimleri engeller.</span><span class="sxs-lookup"><span data-stu-id="c8b92-147">Prevents excessive `using` statements in the `Program` or `Startup` classes where these extension methods are typically called.</span></span>

<span data-ttu-id="c8b92-148">Uygulama:</span><span class="sxs-lookup"><span data-stu-id="c8b92-148">The app:</span></span>

- <span data-ttu-id="c8b92-149"><xref:Microsoft.Extensions.Hosting.IHostBuilder> [Varsayılan bağlayıcı ayarlarına](generic-host.md#default-builder-settings)sahip bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8b92-149">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="c8b92-150">Hizmetleri yapılandırır ve bunlara karşılık gelen hizmet ömrüne ekler.</span><span class="sxs-lookup"><span data-stu-id="c8b92-150">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="c8b92-151"><xref:Microsoft.Extensions.Hosting.IHostBuilder.Build>Bir örneğini çağırır ve atar <xref:Microsoft.Extensions.Hosting.IHost> .</span><span class="sxs-lookup"><span data-stu-id="c8b92-151">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="c8b92-152">Çağrılar `ExemplifyScoping` , öğesini geçirme <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c8b92-152">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="c8b92-153">Sonuç</span><span class="sxs-lookup"><span data-stu-id="c8b92-153">Conclusion</span></span>

<span data-ttu-id="c8b92-154">Uygulama, aşağıdaki örneğe benzer bir çıktı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c8b92-154">The app displays output similar to the following example:</span></span>

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

<span data-ttu-id="c8b92-155">Uygulama çıktısından aşağıdakileri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8b92-155">From the app output, you can see that:</span></span>

- <span data-ttu-id="c8b92-156">Transient işlemler her zaman farklıdır, hizmetin her alımı ile yeni bir örnek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8b92-156">Transient operations are always different, a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="c8b92-157">Scoped işlemler yalnızca yeni bir kapsamla değiştirilir, ancak bir kapsam içinde aynı örneğidir.</span><span class="sxs-lookup"><span data-stu-id="c8b92-157">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="c8b92-158">Singleton işlemler her zaman aynıdır, yeni bir örnek yalnızca bir kez oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8b92-158">Singleton operations are always the same, a new instance is only created once.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8b92-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8b92-159">See also</span></span>

* [<span data-ttu-id="c8b92-160">Bağımlılık ekleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c8b92-160">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
* [<span data-ttu-id="c8b92-161">ASP.NET Core bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="c8b92-161">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
