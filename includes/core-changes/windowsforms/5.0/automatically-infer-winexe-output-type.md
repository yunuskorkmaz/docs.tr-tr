---
ms.openlocfilehash: 54bee14f6de409550357194e905b6ee5d8ef8f18
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679011"
---
### <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="20d13-101">OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="20d13-101">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="20d13-102">`OutputType``WinExe`Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar için otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="20d13-102">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="20d13-103">Ne zaman `OutputType` ayarlandığında `WinExe` , Uygulama yürütüldüğünde konsol penceresi açılmaz.</span><span class="sxs-lookup"><span data-stu-id="20d13-103">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="20d13-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="20d13-104">Change description</span></span>

<span data-ttu-id="20d13-105">Önceki .NET sürümlerinde, proje dosyasında için belirtilen değer `OutputType` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20d13-105">In previous versions of .NET, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="20d13-106">Örnek:</span><span class="sxs-lookup"><span data-stu-id="20d13-106">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="20d13-107">.NET 5,0 ' den itibaren, `OutputType` `WinExe` WPF ve Windows Forms uygulamaları için otomatik olarak olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="20d13-107">Starting in .NET 5.0, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps.</span></span> <span data-ttu-id="20d13-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="20d13-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

#### <a name="reason-for-change"></a><span data-ttu-id="20d13-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="20d13-109">Reason for change</span></span>

<span data-ttu-id="20d13-110">Çoğu kullanıcının bir WPF veya Windows Forms uygulaması yürütüldüğünde konsol penceresinin açılmasını istemediğiniz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="20d13-110">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="20d13-111">Ayrıca, [artık bu uygulama türleri](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) Windows Masaüstü SDK 'sı yerıne .NET SDK 'yı kullandığına göre, doğru varsayılan değer ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="20d13-111">In addition, [now that these application types use the .NET SDK](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="20d13-112">Ayrıca, iOS ve Android 'i hedeflemek için destek eklendiğinde, hepsi aynı çıkış türünü kullanıyorsa, birden çok platform arasında çoklu hedefe daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="20d13-112">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="20d13-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="20d13-113">Version introduced</span></span>

<span data-ttu-id="20d13-114">.NET 5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="20d13-114">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="20d13-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="20d13-115">Recommended action</span></span>

<span data-ttu-id="20d13-116">Sizin bölüminizdeki herhangi bir eylem gerekmiyor.</span><span class="sxs-lookup"><span data-stu-id="20d13-116">No action is required in your part.</span></span> <span data-ttu-id="20d13-117">Ancak, eski davranışa dönmek istiyorsanız, `DisableWinExeOutputInference` özelliği `true` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20d13-117">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

#### <a name="category"></a><span data-ttu-id="20d13-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="20d13-118">Category</span></span>

- <span data-ttu-id="20d13-119">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20d13-119">Windows Forms</span></span>
- <span data-ttu-id="20d13-120">Windows Presentation Framework (WPF)</span><span class="sxs-lookup"><span data-stu-id="20d13-120">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="20d13-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="20d13-121">Affected APIs</span></span>

<span data-ttu-id="20d13-122">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="20d13-122">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
