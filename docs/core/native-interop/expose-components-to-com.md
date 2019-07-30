---
title: .NET Core Bileşenlerini COM’da Gösterme
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 33574eeac5b1f7aa2067b1974f3f2e68fb22e8ff
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631130"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="92b01-102">.NET Core Bileşenlerini COM’da Gösterme</span><span class="sxs-lookup"><span data-stu-id="92b01-102">Exposing .NET Core Components to COM</span></span>

<span data-ttu-id="92b01-103">.NET Core 'da, .NET nesnelerinizi COM 'a sunma süreci, .NET Framework karşılaştırmaya kıyasla önemli ölçüde basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="92b01-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="92b01-104">Aşağıdaki süreç, bir sınıfı COM 'a nasıl kullanıma sunabileceğiniz konusunda size yol gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="92b01-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="92b01-105">Bu öğreticide nasıl yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92b01-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="92b01-106">.NET Core 'dan COM 'a bir sınıf sunun.</span><span class="sxs-lookup"><span data-stu-id="92b01-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="92b01-107">.NET Core kitaplığınızı oluşturmanın bir parçası olarak bir COM sunucusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92b01-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="92b01-108">Kayıt defteri ücretsiz COM için otomatik olarak yan yana sunucu bildirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92b01-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="92b01-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="92b01-109">Prerequisites</span></span>

- <span data-ttu-id="92b01-110">[.NET Core 3,0 Preview 7 SDK 'sını](https://www.microsoft.com/net/core) veya daha yeni bir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="92b01-110">Install the [.NET Core 3.0 Preview 7 SDK](https://www.microsoft.com/net/core) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="92b01-111">Kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="92b01-111">Create the library</span></span>

<span data-ttu-id="92b01-112">İlk adım, kitaplığı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="92b01-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="92b01-113">Yeni bir klasör oluşturun ve bu klasörde ' i çalıştırın `dotnet new classlib`.</span><span class="sxs-lookup"><span data-stu-id="92b01-113">Create a new folder, and in that folder run `dotnet new classlib`.</span></span>
2. <span data-ttu-id="92b01-114">Açık `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="92b01-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="92b01-115">Dosyanın `using System.Runtime.InteropServices;` en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92b01-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="92b01-116">Adlı `IServer`bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92b01-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="92b01-117">Örneğin:[!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span><span class="sxs-lookup"><span data-stu-id="92b01-117">For example: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span></span>
5. <span data-ttu-id="92b01-118">`[Guid("<IID>")]` Öğesini, uygulamayı uyguladığınız com arabirimi için arabirim GUID 'i ile birlikte arabirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92b01-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="92b01-119">Örneğin: `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="92b01-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="92b01-120">Bu GUID 'nin COM için bu arabirimin tek tanımlayıcısı olduğundan, bu GUID 'in benzersiz olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92b01-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="92b01-121">Visual Studio 'da, GUID oluştur ' a giderek bir GUID oluşturabilirsiniz > Guid Oluştur aracını açın.</span><span class="sxs-lookup"><span data-stu-id="92b01-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="92b01-122">`[InterfaceType]` Arabirimine özniteliği ekleyin ve arabiriminizdeki hangi temel com arabirimlerini uygulanacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="92b01-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="92b01-123">`Server` Uygulayan`IServer`adlı bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92b01-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="92b01-124">`[Guid("<CLSID>")]` Öğesini, uyguladığınız com sınıfı için sınıf tanımlayıcısı GUID 'i ile sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92b01-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="92b01-125">Örneğin: `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="92b01-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="92b01-126">Arabirim GUID 'SI ile olduğu gibi bu GUID, bu arabirimin COM için tek tanımlayıcısı olduğundan benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92b01-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="92b01-127">`[ComVisible(true)]` Özniteliğini hem arabirimine hem de sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92b01-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="92b01-128">.NET Framework aksine, .NET Core, COM üzerinden etkinleştirilebilir olmasını istediğiniz herhangi bir sınıfın CLSID 'sini belirtmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="92b01-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="92b01-129">COM konağını oluşturma</span><span class="sxs-lookup"><span data-stu-id="92b01-129">Generate the COM host</span></span>

1. <span data-ttu-id="92b01-130">Proje dosyasını açın ve `<PropertyGroup></PropertyGroup>` etiketinin içine `<EnableComHosting>true</EnableComHosting>` ekleyin. `.csproj`</span><span class="sxs-lookup"><span data-stu-id="92b01-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="92b01-131">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92b01-131">Build the project.</span></span>

<span data-ttu-id="92b01-132">`ProjectName.dll`Elde edilen çıktıda bir `ProjectName.deps.json` `ProjectName.runtimeconfig.json` , ve`ProjectName.comhost.dll` dosyası olacaktır.</span><span class="sxs-lookup"><span data-stu-id="92b01-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="92b01-133">Com için COM ana bilgisayarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="92b01-133">Register the COM host for COM</span></span>

<span data-ttu-id="92b01-134">Yükseltilmiş bir komut istemi açın ve çalıştırın `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="92b01-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="92b01-135">Bu, tüm sunulan .NET nesnelerinizi COM ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="92b01-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="92b01-136">RegFree COM etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="92b01-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="92b01-137">Proje dosyasını açın ve `<PropertyGroup></PropertyGroup>` etiketinin içine `<EnableRegFreeCom>true</EnableRegFreeCom>` ekleyin. `.csproj`</span><span class="sxs-lookup"><span data-stu-id="92b01-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="92b01-138">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92b01-138">Build the project.</span></span>

<span data-ttu-id="92b01-139">Sonuçta elde edilen çıkışın bir `ProjectName.X.manifest` dosyası da olacaktır.</span><span class="sxs-lookup"><span data-stu-id="92b01-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="92b01-140">Bu dosya, kayıt defteri-ücretsiz COM ile kullanılmak üzere yan yana bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="92b01-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="92b01-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="92b01-141">Sample</span></span>

<span data-ttu-id="92b01-142">GitHub 'daki DotNet/Samples deposunda tam işlevli bir [com sunucusu örneği](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) vardır.</span><span class="sxs-lookup"><span data-stu-id="92b01-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="92b01-143">Ek notlar</span><span class="sxs-lookup"><span data-stu-id="92b01-143">Additional Notes</span></span>

<span data-ttu-id="92b01-144">.NET Framework aksine bir .NET Core derlemesinden COM tür kitaplığı (TLB) oluşturmaya yönelik .NET Core desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="92b01-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="92b01-145">Arabirimlerinizin yerel bildirimleri için el ile bir IDL dosyası ya da C++ bir üst bilgi yazmanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="92b01-145">You will either have to manually write an IDL file or a C++ header for the native declarations of your interfaces.</span></span>

<span data-ttu-id="92b01-146">Ayrıca, hem .NET Framework hem de .NET Core 'u aynı işleme yüklemek desteklenmez ve bir .NET Core COM sunucusunun bir .NET Framework COM istemci işlemine yüklenmesi veya tam tersi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="92b01-146">Additionally, loading both .NET Framework and .NET Core into the same process is unsupported, and as a result loading a .NET Core COM server into a .NET Framework COM client process or vice versa is not supported.</span></span>
