---
title: .NET Core bileşenlerinin COM'a teşhir edilmesi
description: Bu öğretici, .NET Core'dan bir sınıfı COM'a nasıl gösteriş yapacaklarını gösterir. Kayıt Defteri'ne Göre COM sunucusu ve yan yana bir sunucu bildirimi oluşturursunuz.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 17d85b9e9734fae0bb69f94da8c08669216ab0ae
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242874"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="4adce-104">.NET Core bileşenlerinin COM'a teşhir edilmesi</span><span class="sxs-lookup"><span data-stu-id="4adce-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="4adce-105">.NET Core'da,.NET nesnelerinizi COM'a teşhir etme işlemi .NET Framework ile karşılaştırıldığında önemli ölçüde kolaylaştırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4adce-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="4adce-106">Aşağıdaki işlem, bir sınıfı COM'a nasıl maruz bırakacağınız konusunda size yol gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="4adce-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="4adce-107">Bu öğretici şunların nasıl yapıldığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4adce-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="4adce-108">.NET Core'dan bir sınıfı COM'a gösterin.</span><span class="sxs-lookup"><span data-stu-id="4adce-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="4adce-109">.NET Core kitaplığınızı oluşturmanın bir parçası olarak bir COM sunucusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4adce-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="4adce-110">Kayıt Defteri'ne Göre Com için yan yana bir sunucu bildirimi otomatik olarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4adce-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4adce-111">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="4adce-111">Prerequisites</span></span>

- <span data-ttu-id="4adce-112">[.NET Core 3.0 SDK'yı](https://dotnet.microsoft.com/download) veya daha yeni bir sürümü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="4adce-113">Kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="4adce-113">Create the library</span></span>

<span data-ttu-id="4adce-114">İlk adım kitaplık oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="4adce-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="4adce-115">Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4adce-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="4adce-116">`Class1.cs` dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="4adce-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="4adce-117">Dosyanın üstüne ekleyin. `using System.Runtime.InteropServices;`</span><span class="sxs-lookup"><span data-stu-id="4adce-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="4adce-118">Adlı `IServer`bir arayüz oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4adce-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="4adce-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4adce-119">For example:</span></span>

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

5. <span data-ttu-id="4adce-120">Uyguladığınız `[Guid("<IID>")]` COM arabirimi için GUID arabirimi ile arabirime özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="4adce-121">Örneğin, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="4adce-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="4adce-122">BU ARABIRIMIN COM için tek tanımlayıcısı olduğundan, bu GUID'nin benzersiz olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4adce-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="4adce-123">Visual Studio'da, GUID oluştur aracını açmak için Araçlar > GUID Oluştur'a giderek bir GUID oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4adce-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="4adce-124">`[InterfaceType]` Arabirime özniteliği ekleyin ve arabiriminizin hangi temel COM arabirimlerini uygulaması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="4adce-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="4adce-125">'yi uygulayan `Server` bir sınıf oluşturun. `IServer`</span><span class="sxs-lookup"><span data-stu-id="4adce-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="4adce-126">`[Guid("<CLSID>")]` Uygulamakta olduğunuz COM sınıfı için sınıf tanımlayıcısı GUID ile sınıfa özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="4adce-127">Örneğin, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="4adce-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="4adce-128">Bu arabirimin COM'a tek tanımlayıcısı olduğundan, bu GUID arabiriminde olduğu gibi benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4adce-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="4adce-129">`[ComVisible(true)]` Özniteliği hem arabirime hem de sınıfa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4adce-130">.NET Framework'ün aksine,.NET Core, COM aracılığıyla etkinleştirilebilir olmasını istediğiniz herhangi bir sınıfın CLSID'sini belirtmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4adce-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="4adce-131">COM ana bilgisayarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="4adce-131">Generate the COM host</span></span>

1. <span data-ttu-id="4adce-132">Proje `.csproj` dosyasını açın `<EnableComHosting>true</EnableComHosting>` ve `<PropertyGroup></PropertyGroup>` etiketin içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="4adce-133">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-133">Build the project.</span></span>

<span data-ttu-id="4adce-134">Elde edilen çıktı , `ProjectName.dll` `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` `ProjectName.comhost.dll` ve dosya olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4adce-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="4adce-135">COM ana bilgisayarını COM için kaydedin</span><span class="sxs-lookup"><span data-stu-id="4adce-135">Register the COM host for COM</span></span>

<span data-ttu-id="4adce-136">Yükseltilmiş bir komut istemini `regsvr32 ProjectName.comhost.dll`açın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4adce-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="4adce-137">Bu, tüm maruz kalan .NET nesnelerinizi COM'a kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4adce-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="4adce-138">RegFree COM'u etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4adce-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="4adce-139">Proje `.csproj` dosyasını açın `<EnableRegFreeCom>true</EnableRegFreeCom>` ve `<PropertyGroup></PropertyGroup>` etiketin içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="4adce-140">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="4adce-140">Build the project.</span></span>

<span data-ttu-id="4adce-141">Elde edilen çıktı artık bir `ProjectName.X.manifest` dosyaya da sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4adce-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="4adce-142">Bu dosya, Kayıt Defteri-Free COM ile kullanılmak üzere yan yana tezahürüdür.</span><span class="sxs-lookup"><span data-stu-id="4adce-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="4adce-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="4adce-143">Sample</span></span>

<span data-ttu-id="4adce-144">GitHub'daki dotnet/numune deposunda tam işlevsel bir [COM sunucu örneği](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) vardır.</span><span class="sxs-lookup"><span data-stu-id="4adce-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="4adce-145">Ek notlar</span><span class="sxs-lookup"><span data-stu-id="4adce-145">Additional notes</span></span>

<span data-ttu-id="4adce-146">.NET Framework'ün aksine, .NET Core derlemesinden BIR COM Türü Kitaplığı (TLB) oluşturmak için .NET Core'da destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="4adce-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="4adce-147">Kılavuz, COM arabirimlerinin yerel bildirimleri için bir IDL dosyasını veya C/C++ üstbilgisini el ile yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="4adce-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="4adce-148">COM bileşenlerinin [bağımsız dağıtımları](../deploying/index.md#publish-self-contained) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4adce-148">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="4adce-149">Com bileşenlerinin yalnızca [çalışma süresine bağlı dağıtımları](../deploying/index.md#publish-runtime-dependent) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4adce-149">Only [runtime-dependent deployments](../deploying/index.md#publish-runtime-dependent) of COM components are supported.</span></span>

<span data-ttu-id="4adce-150">Ayrıca, hem .NET Framework hem de .NET Core'un aynı işleme yüklenmesi tanılama sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="4adce-150">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="4adce-151">Hem .NET Framework hem de .NET Core'u aynı anda hata ayıklamak mümkün olmadığı için, birincil sınırlama yönetilen bileşenlerin hata ayıklanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="4adce-151">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="4adce-152">Buna ek olarak, iki çalışma zamanı örneği yönetilen derlemeleri paylaşmaz.</span><span class="sxs-lookup"><span data-stu-id="4adce-152">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="4adce-153">Bu, gerçek .NET türlerini iki çalışma zamanında paylaşmanın mümkün olmadığı ve bunun yerine tüm etkileşimlerin açıklanmış COM arabirim sözleşmeleri ile sınırlandırılması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4adce-153">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
