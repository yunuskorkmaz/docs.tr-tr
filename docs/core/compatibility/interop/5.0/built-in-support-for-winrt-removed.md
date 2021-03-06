---
title: "Son değişiklik: WinRT için yerleşik destek .NET 'ten kaldırılmıştır"
description: .NET 5 ' teki birlikte çalışma için yerleşik desteğin .NET 'ten kaldırıldığı hakkında bilgi edinin.
ms.date: 10/13/2020
ms.openlocfilehash: 986b810b74c7e7d7514ec2b734bfab45e29b87fa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256692"
---
# <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="271ac-103">WinRT için yerleşik destek .NET 'ten kaldırılmıştır</span><span class="sxs-lookup"><span data-stu-id="271ac-103">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="271ac-104">.NET 'te [Windows çalışma zamanı (WinRT)](/uwp/winrt-cref/winrt-type-system) API 'leri tüketimi için yerleşik destek kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="271ac-104">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="271ac-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="271ac-105">Version introduced</span></span>

<span data-ttu-id="271ac-106">5.0</span><span class="sxs-lookup"><span data-stu-id="271ac-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="271ac-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="271ac-107">Change description</span></span>

<span data-ttu-id="271ac-108">Daha önce CoreCLR, etkin ve WinRT türlerini tüketen [Windows meta verileri (WinMD) dosyalarını](/uwp/winrt-cref/winmd-files) tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="271ac-108">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="271ac-109">.NET 5 ' den başlayarak CoreCLR artık WinMD dosyalarını doğrudan tüketmez.</span><span class="sxs-lookup"><span data-stu-id="271ac-109">Starting in .NET 5, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="271ac-110">Desteklenmeyen bir derlemeye başvuru yapmaya çalışırsanız, bir ile karşılaşırsınız <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="271ac-110">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="271ac-111">Bir WinRT sınıfını etkinleştirirseniz bir ile karşılaşırsınız <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="271ac-111">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="271ac-112">Bu son değişiklik aşağıdaki nedenlerden dolayı yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="271ac-112">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="271ac-113">Bu nedenle, WinRT .NET çalışma zamanından ayrı olarak geliştirilebilir ve artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="271ac-113">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="271ac-114">İOS ve Android gibi diğer işletim sistemleri için sunulan birlikte çalışma sistemlerine sahip simetri için.</span><span class="sxs-lookup"><span data-stu-id="271ac-114">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="271ac-115">C# özellikleri, ara dil (IL) bağlama ve zaman içinde (AOT) derleme gibi diğer .NET özelliklerinden yararlanmak için.</span><span class="sxs-lookup"><span data-stu-id="271ac-115">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="271ac-116">.NET çalışma zamanı kod temelinin basitleşmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="271ac-116">To simplify the .NET runtime codebase.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="271ac-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="271ac-117">Recommended action</span></span>

- <span data-ttu-id="271ac-118">[Microsoft. Windows. SDK. Contracts paketine](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)başvuruları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="271ac-118">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span></span>  <span data-ttu-id="271ac-119">Bunun yerine, projenin özelliği aracılığıyla erişmek istediğiniz Windows API 'lerinin sürümünü belirtin `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="271ac-119">Instead, specify the version of the Windows APIs that you want to access via the `TargetFramework` property of the project.</span></span>  <span data-ttu-id="271ac-120">Örnek:</span><span class="sxs-lookup"><span data-stu-id="271ac-120">For example:</span></span>

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- <span data-ttu-id="271ac-121">.NET 5 ve sonraki sürümler için WinRT API 'Leri ve türleri oluşturmak veya özelleştirmek üzere [C#/wınrt](/windows/uwp/csharp-winrt/) araç zincirini kullanın.</span><span class="sxs-lookup"><span data-stu-id="271ac-121">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types for .NET 5 and later versions.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="271ac-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="271ac-122">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

### Category

Interop

-->
