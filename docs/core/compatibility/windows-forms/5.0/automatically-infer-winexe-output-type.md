---
title: 'Son değişiklik: WPF ve WinForms uygulamaları için OutputType, WinExe olarak ayarlanmıştır'
description: Windows Forms uygulamalar için OutputType 'nin otomatik olarak WinExe olarak ayarlandığı .NET SDK 5.0.100 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 02/08/2021
ms.openlocfilehash: 565007e9ce6be289456afc9facbd4c555a1110bd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256197"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="69d0a-103">OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="69d0a-103">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="69d0a-104">`OutputType``WinExe`Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar için otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="69d0a-104">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="69d0a-105">Ne zaman `OutputType` ayarlandığında `WinExe` , Uygulama yürütüldüğünde konsol penceresi açılmaz.</span><span class="sxs-lookup"><span data-stu-id="69d0a-105">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

## <a name="change-description"></a><span data-ttu-id="69d0a-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="69d0a-106">Change description</span></span>

<span data-ttu-id="69d0a-107">.NET SDK 'sının önceki sürümlerinde, proje dosyasında için belirtilen değer `OutputType` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69d0a-107">In previous versions of the .NET SDK, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="69d0a-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="69d0a-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="69d0a-109">.NET SDK 'nın 5.0.100 sürümünden itibaren, olarak `OutputType` ayarlandığında `Exe` ,, `WinExe` .NET Framework dahil olmak üzere tüm Framework sürümlerini hedefleyen WPF ve Windows Forms uygulamalar için otomatik olarak olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="69d0a-109">Starting in the 5.0.100 version of the .NET SDK, when `OutputType` is set to `Exe`, it is automatically changed to `WinExe` for WPF and Windows Forms apps that target any framework version, including .NET Framework.</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

 <span data-ttu-id="69d0a-110">`OutputType`Proje dosyasında belirtilmemişse, varsayılan olarak `Library` Bu değer değişmez.</span><span class="sxs-lookup"><span data-stu-id="69d0a-110">If `OutputType` is not specified in the project file, it defaults to `Library` and that value doesn't change.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="69d0a-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="69d0a-111">Reason for change</span></span>

<span data-ttu-id="69d0a-112">Çoğu kullanıcının bir WPF veya Windows Forms uygulaması yürütüldüğünde konsol penceresinin açılmasını istemediğiniz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="69d0a-112">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="69d0a-113">Ayrıca, [artık bu uygulama türleri](sdk-and-target-framework-change.md) Windows Masaüstü SDK 'sı yerıne .NET SDK 'yı kullandığına göre, doğru varsayılan değer ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="69d0a-113">In addition, [now that these application types use the .NET SDK](sdk-and-target-framework-change.md) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="69d0a-114">Ayrıca, iOS ve Android 'i hedeflemek için destek eklendiğinde, hepsi aynı çıkış türünü kullanıyorsa, birden çok platform arasında çoklu hedefe daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="69d0a-114">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="69d0a-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="69d0a-115">Version introduced</span></span>

<span data-ttu-id="69d0a-116">.NET 5.0.100</span><span class="sxs-lookup"><span data-stu-id="69d0a-116">.NET 5.0.100</span></span>

## <a name="recommended-action"></a><span data-ttu-id="69d0a-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="69d0a-117">Recommended action</span></span>

<span data-ttu-id="69d0a-118">Sizin bölüminizdeki herhangi bir eylem gerekmiyor.</span><span class="sxs-lookup"><span data-stu-id="69d0a-118">No action is required in your part.</span></span> <span data-ttu-id="69d0a-119">Ancak, eski davranışa dönmek istiyorsanız, `DisableWinExeOutputInference` özelliği `true` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="69d0a-119">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a><span data-ttu-id="69d0a-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="69d0a-120">Affected APIs</span></span>

<span data-ttu-id="69d0a-121">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="69d0a-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
