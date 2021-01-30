---
title: .NET Core bileşenlerini COM 'a gösterme
description: Bu öğreticide, .NET Core 'dan bir sınıfın COM 'a nasıl sunulebileceği gösterilmektedir. Registry-Free COM için bir COM sunucusu ve yan yana sunucu bildirimi oluşturabilirsiniz.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 13c91e5cb6728c5669642d1b5f7bb461efdd44f8
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065057"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="245fa-104">.NET Core bileşenlerini COM 'a gösterme</span><span class="sxs-lookup"><span data-stu-id="245fa-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="245fa-105">.NET Core 'da, .NET nesnelerinizi COM 'a sunma süreci, .NET Framework karşılaştırmaya kıyasla önemli ölçüde basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="245fa-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="245fa-106">Aşağıdaki süreç, bir sınıfı COM 'a nasıl kullanıma sunabileceğiniz konusunda size yol gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="245fa-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="245fa-107">Bu öğretici şunların nasıl yapıldığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="245fa-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="245fa-108">.NET Core 'dan COM 'a bir sınıf sunun.</span><span class="sxs-lookup"><span data-stu-id="245fa-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="245fa-109">.NET Core kitaplığınızı oluşturmanın bir parçası olarak bir COM sunucusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="245fa-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="245fa-110">Registry-Free COM için otomatik olarak yan yana sunucu bildirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="245fa-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="245fa-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="245fa-111">Prerequisites</span></span>

- <span data-ttu-id="245fa-112">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download) veya daha yeni bir sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="245fa-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="245fa-113">Kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="245fa-113">Create the library</span></span>

<span data-ttu-id="245fa-114">İlk adım, kitaplığı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="245fa-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="245fa-115">Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="245fa-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="245fa-116">`Class1.cs` dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="245fa-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="245fa-117">`using System.Runtime.InteropServices;`Dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="245fa-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="245fa-118">Adlı bir arabirim oluşturun `IServer` .</span><span class="sxs-lookup"><span data-stu-id="245fa-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="245fa-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="245fa-119">For example:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. <span data-ttu-id="245fa-120">`[Guid("<IID>")]`Öğesini, uygulamayı UYGULADıĞıNıZ com arabirimi için ARABIRIM GUID 'i ile birlikte arabirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="245fa-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="245fa-121">Örneğin, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="245fa-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="245fa-122">Bu GUID 'nin COM için bu arabirimin tek tanımlayıcısı olduğundan, bu GUID 'in benzersiz olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="245fa-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="245fa-123">Visual Studio 'da, GUID oluştur ' a giderek bir GUID oluşturabilirsiniz > Guid Oluştur aracını açın.</span><span class="sxs-lookup"><span data-stu-id="245fa-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="245fa-124">`[InterfaceType]`Arabirimine özniteliği ekleyin ve arabiriminizdeki hangi temel com arabirimlerini uygulanacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="245fa-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="245fa-125">Uygulayan adlı bir sınıf oluşturun `Server` `IServer` .</span><span class="sxs-lookup"><span data-stu-id="245fa-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="245fa-126">`[Guid("<CLSID>")]`Öğesini, UYGULADıĞıNıZ com sınıfı için sınıf tanımlayıcısı GUID 'i ile sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="245fa-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="245fa-127">Örneğin, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="245fa-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="245fa-128">Arabirim GUID 'SI ile olduğu gibi bu GUID, bu arabirimin COM için tek tanımlayıcısı olduğundan benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="245fa-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="245fa-129">`[ComVisible(true)]`Özniteliğini hem arabirimine hem de sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="245fa-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="245fa-130">.NET Framework aksine, .NET Core, COM üzerinden etkinleştirilebilir olmasını istediğiniz herhangi bir sınıfın CLSID 'sini belirtmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="245fa-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="245fa-131">COM konağını oluşturma</span><span class="sxs-lookup"><span data-stu-id="245fa-131">Generate the COM host</span></span>

1. <span data-ttu-id="245fa-132">`.csproj`Proje dosyasını açın ve `<EnableComHosting>true</EnableComHosting>` etiketinin içine ekleyin `<PropertyGroup></PropertyGroup>` .</span><span class="sxs-lookup"><span data-stu-id="245fa-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="245fa-133">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="245fa-133">Build the project.</span></span>

<span data-ttu-id="245fa-134">Elde edilen çıktıda bir `ProjectName.dll` , `ProjectName.deps.json` `ProjectName.runtimeconfig.json` ve `ProjectName.comhost.dll` dosyası olacaktır.</span><span class="sxs-lookup"><span data-stu-id="245fa-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="245fa-135">Com için COM ana bilgisayarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="245fa-135">Register the COM host for COM</span></span>

<span data-ttu-id="245fa-136">Yükseltilmiş bir komut istemi açın ve çalıştırın `regsvr32 ProjectName.comhost.dll` .</span><span class="sxs-lookup"><span data-stu-id="245fa-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="245fa-137">Bu, tüm sunulan .NET nesnelerinizi COM ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="245fa-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="245fa-138">RegFree COM etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="245fa-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="245fa-139">`.csproj`Proje dosyasını açın ve `<EnableRegFreeCom>true</EnableRegFreeCom>` etiketinin içine ekleyin `<PropertyGroup></PropertyGroup>` .</span><span class="sxs-lookup"><span data-stu-id="245fa-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="245fa-140">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="245fa-140">Build the project.</span></span>

<span data-ttu-id="245fa-141">Sonuçta elde edilen çıkışın bir dosyası da olacaktır `ProjectName.X.manifest` .</span><span class="sxs-lookup"><span data-stu-id="245fa-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="245fa-142">Bu dosya, Registry-Free COM ile kullanım için yan yana bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="245fa-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="245fa-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="245fa-143">Sample</span></span>

<span data-ttu-id="245fa-144">GitHub 'daki DotNet/Samples deposunda tam işlevli bir [com sunucusu örneği](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) vardır.</span><span class="sxs-lookup"><span data-stu-id="245fa-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="245fa-145">Ek notlar</span><span class="sxs-lookup"><span data-stu-id="245fa-145">Additional notes</span></span>

<span data-ttu-id="245fa-146">.NET Framework aksine bir .NET Core derlemesinden COM tür kitaplığı (TLB) oluşturmaya yönelik .NET Core desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="245fa-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="245fa-147">Bu kılavuz, COM arabirimlerinin yerel bildirimleri için el ile bir IDL dosyası ya da C/C++ üst bilgisi yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="245fa-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="245fa-148">.NET Framework, "herhangi bir CPU" derlemesi, hem 32-bit hem de 64-bit istemciler tarafından tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="245fa-148">In .NET Framework, an "Any CPU" assembly can be consumed by both 32-bit and 64-bit clients.</span></span> <span data-ttu-id="245fa-149">Varsayılan olarak, .NET Core, .NET 5 ve sonraki sürümlerinde, "Any CPU" Derlemeleriyle birlikte 64 bit *\*.comhost.dll* vardır.</span><span class="sxs-lookup"><span data-stu-id="245fa-149">By default, in .NET Core, .NET 5, and later versions, "Any CPU" assemblies are accompanied by a 64-bit *\*.comhost.dll*.</span></span> <span data-ttu-id="245fa-150">Bu nedenle, yalnızca 64 bitlik istemciler tarafından tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="245fa-150">Because of this, they can only be consumed by 64-bit clients.</span></span> <span data-ttu-id="245fa-151">Bu varsayılandır çünkü SDK 'nın gösterdiği şeydir.</span><span class="sxs-lookup"><span data-stu-id="245fa-151">That is the default because that is what the SDK represents.</span></span> <span data-ttu-id="245fa-152">Bu davranış, "kendinden bağımsız" özelliğin Yayımlanma biçimi ile aynıdır: varsayılan olarak SDK 'nın sağladığı öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="245fa-152">This behavior is identical to how the "self-contained" feature is published: by default it uses what the SDK provides.</span></span> <span data-ttu-id="245fa-153">`NETCoreSdkRuntimeIdentifier`MSBuild özelliği *\*.comhost.dll* bit durumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="245fa-153">The `NETCoreSdkRuntimeIdentifier` MSBuild property determines the bitness of *\*.comhost.dll*.</span></span> <span data-ttu-id="245fa-154">Yönetilen bölüm aslında beklenen şekilde bittik, ancak eşlik eden yerel varlık, hedeflenen SDK 'ya varsayılan olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="245fa-154">The managed part is actually bitness agnostic as expected, but the accompanying native asset defaults to the targeted SDK.</span></span>

<span data-ttu-id="245fa-155">COM bileşenlerinin [kendi kendine kapsanan dağıtımları](../deploying/index.md#publish-self-contained) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="245fa-155">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="245fa-156">Yalnızca [çerçeveye BAĞıMLı](../deploying/index.md#publish-framework-dependent) com bileşenleri dağıtımları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="245fa-156">Only [framework-dependent deployments](../deploying/index.md#publish-framework-dependent) of COM components are supported.</span></span>

<span data-ttu-id="245fa-157">Ayrıca, hem .NET Framework hem de .NET Core 'u aynı işleme yüklemek için tanılama sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="245fa-157">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="245fa-158">Aynı anda hem .NET Framework hem de .NET Core hata ayıklaması mümkün olmadığından, birincil sınırlama yönetilen bileşenlerin hata ayıklaması olur.</span><span class="sxs-lookup"><span data-stu-id="245fa-158">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="245fa-159">Ayrıca, iki çalışma zamanı örneği yönetilen derlemeleri paylaşmaz.</span><span class="sxs-lookup"><span data-stu-id="245fa-159">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="245fa-160">Diğer bir deyişle, gerçek .NET türlerini iki çalışma sırasında paylaşmak mümkün değildir ve bunun yerine tüm etkileşimler sunulan COM arabirimi sözleşmeleri ile sınırlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="245fa-160">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
