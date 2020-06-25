---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365667"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="4c617-101">WinRT için yerleşik destek .NET 'ten kaldırılmıştır</span><span class="sxs-lookup"><span data-stu-id="4c617-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="4c617-102">.NET 'te [Windows çalışma zamanı (WinRT)](/uwp/winrt-cref/winrt-type-system) API 'leri tüketimi için yerleşik destek kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4c617-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4c617-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4c617-103">Version introduced</span></span>

<span data-ttu-id="4c617-104">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="4c617-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="4c617-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4c617-105">Change description</span></span>

<span data-ttu-id="4c617-106">Daha önce CoreCLR, etkin ve WinRT türlerini tüketen [Windows meta verileri (WinMD) dosyalarını](/uwp/winrt-cref/winmd-files) tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="4c617-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="4c617-107">.NET 5,0 ' den başlayarak CoreCLR artık WinMD dosyalarını doğrudan tüketmez.</span><span class="sxs-lookup"><span data-stu-id="4c617-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="4c617-108">Desteklenmeyen bir derlemeye başvuru yapmaya çalışırsanız, bir ile karşılaşırsınız <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="4c617-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="4c617-109">Bir WinRT sınıfını etkinleştirirseniz bir ile karşılaşırsınız <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="4c617-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="4c617-110">Bu son değişiklik aşağıdaki nedenlerden dolayı yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="4c617-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="4c617-111">Bu nedenle, WinRT .NET çalışma zamanından ayrı olarak geliştirilebilir ve artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c617-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="4c617-112">İOS ve Android gibi diğer işletim sistemleri için sunulan birlikte çalışma sistemlerine sahip simetri için.</span><span class="sxs-lookup"><span data-stu-id="4c617-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="4c617-113">C# özellikleri, ara dil (IL) bağlama ve zaman içinde (AOT) derleme gibi diğer .NET özelliklerinden yararlanmak için.</span><span class="sxs-lookup"><span data-stu-id="4c617-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="4c617-114">.NET çalışma zamanı kod temelinin basitleşmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c617-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4c617-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4c617-115">Recommended action</span></span>

- <span data-ttu-id="4c617-116">[Microsoft. Windows. SDK. Contracts paketine](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) başvuruları kaldırın ve [Microsoft.Windows.SDK.net paketine](https://www.nuget.org/packages/microsoft.windows.sdk.net)yönelik başvurularla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4c617-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) and replace them with references to the [Microsoft.Windows.SDK.NET package](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span></span>

- <span data-ttu-id="4c617-117">.NET 5,0 ve sonraki sürümlerde WinRT API 'Leri ve türlerini oluşturmak veya özelleştirmek için [C#/wınrt](/windows/uwp/csharp-winrt/) araç zincirini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c617-117">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types in .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="4c617-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="4c617-118">Category</span></span>

<span data-ttu-id="4c617-119">Interop</span><span class="sxs-lookup"><span data-stu-id="4c617-119">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4c617-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4c617-120">Affected APIs</span></span>

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
