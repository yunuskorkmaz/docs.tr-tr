---
ms.openlocfilehash: 47c676122df4f0990949a7bfbcd7af8c6144d870
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160559"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="3b34a-101">WinRT için yerleşik destek .NET 'ten kaldırılmıştır</span><span class="sxs-lookup"><span data-stu-id="3b34a-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="3b34a-102">.NET 'te [Windows çalışma zamanı (WinRT)](/uwp/winrt-cref/winrt-type-system) API 'leri tüketimi için yerleşik destek kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3b34a-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3b34a-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3b34a-103">Version introduced</span></span>

<span data-ttu-id="3b34a-104">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="3b34a-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="3b34a-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3b34a-105">Change description</span></span>

<span data-ttu-id="3b34a-106">Daha önce CoreCLR, etkin ve WinRT türlerini tüketen [Windows meta verileri (WinMD) dosyalarını](/uwp/winrt-cref/winmd-files) tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="3b34a-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="3b34a-107">.NET 5,0 ' den başlayarak CoreCLR artık WinMD dosyalarını doğrudan tüketmez.</span><span class="sxs-lookup"><span data-stu-id="3b34a-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="3b34a-108">Desteklenmeyen bir derlemeye başvuru yapmaya çalışırsanız, bir ile karşılaşırsınız <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="3b34a-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="3b34a-109">Bir WinRT sınıfını etkinleştirirseniz bir ile karşılaşırsınız <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="3b34a-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="3b34a-110">Bu son değişiklik aşağıdaki nedenlerden dolayı yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="3b34a-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="3b34a-111">Bu nedenle, WinRT .NET çalışma zamanından ayrı olarak geliştirilebilir ve artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b34a-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="3b34a-112">İOS ve Android gibi diğer işletim sistemleri için sunulan birlikte çalışma sistemlerine sahip simetri için.</span><span class="sxs-lookup"><span data-stu-id="3b34a-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="3b34a-113">C# özellikleri, ara dil (IL) bağlama ve zaman içinde (AOT) derleme gibi diğer .NET özelliklerinden yararlanmak için.</span><span class="sxs-lookup"><span data-stu-id="3b34a-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="3b34a-114">.NET çalışma zamanı kod temelinin basitleşmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b34a-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3b34a-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3b34a-115">Recommended action</span></span>

- <span data-ttu-id="3b34a-116">[Microsoft. Windows. SDK. Contracts paketine](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)başvuruları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3b34a-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span></span>  <span data-ttu-id="3b34a-117">Bunun yerine, projenin özelliği aracılığıyla erişmek istediğiniz Windows API 'lerinin sürümünü belirtin `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="3b34a-117">Instead, specify the version of the Windows APIs that you want to access via the `TargetFramework` property of the project.</span></span>  <span data-ttu-id="3b34a-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3b34a-118">For example:</span></span>

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- <span data-ttu-id="3b34a-119">.NET 5,0 ve üzeri sürümler için WinRT API 'Leri ve türleri oluşturmak veya özelleştirmek üzere [C#/wınrt](/windows/uwp/csharp-winrt/) araç zincirini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b34a-119">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types for .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="3b34a-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="3b34a-120">Category</span></span>

<span data-ttu-id="3b34a-121">Interop</span><span class="sxs-lookup"><span data-stu-id="3b34a-121">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3b34a-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3b34a-122">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
