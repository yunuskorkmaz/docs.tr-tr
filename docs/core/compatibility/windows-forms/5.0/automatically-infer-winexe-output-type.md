---
title: 'Son değişiklik: WPF ve WinForms uygulamaları için OutputType, WinExe olarak ayarlanmıştır'
description: OutputType Windows Forms uygulamalar için otomatik olarak WinExe olarak ayarlandığı .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: 7b2c7a76983c9e7958808e3cc4716be7792841c6
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513191"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="0b522-103">OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="0b522-103">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="0b522-104">`OutputType``WinExe`Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar için otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b522-104">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="0b522-105">Ne zaman `OutputType` ayarlandığında `WinExe` , Uygulama yürütüldüğünde konsol penceresi açılmaz.</span><span class="sxs-lookup"><span data-stu-id="0b522-105">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

## <a name="change-description"></a><span data-ttu-id="0b522-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="0b522-106">Change description</span></span>

<span data-ttu-id="0b522-107">.NET SDK 'sının önceki sürümlerinde, proje dosyasında için belirtilen değer `OutputType` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b522-107">In previous versions of the .NET SDK, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="0b522-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b522-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="0b522-109">.NET SDK 'sının 5.0.1 sürümünden itibaren, `OutputType` `WinExe` .NET Framework dahil olmak üzere tüm Framework SÜRÜMLERINI hedefleyen WPF ve Windows Forms uygulamalar için otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b522-109">Starting in the 5.0.1 version of the .NET SDK, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps that target any framework version, including .NET Framework.</span></span> <span data-ttu-id="0b522-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b522-110">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a><span data-ttu-id="0b522-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0b522-111">Reason for change</span></span>

<span data-ttu-id="0b522-112">Çoğu kullanıcının bir WPF veya Windows Forms uygulaması yürütüldüğünde konsol penceresinin açılmasını istemediğiniz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0b522-112">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="0b522-113">Ayrıca, [artık bu uygulama türleri](sdk-and-target-framework-change.md) Windows Masaüstü SDK 'sı yerıne .NET SDK 'yı kullandığına göre, doğru varsayılan değer ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b522-113">In addition, [now that these application types use the .NET SDK](sdk-and-target-framework-change.md) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="0b522-114">Ayrıca, iOS ve Android 'i hedeflemek için destek eklendiğinde, hepsi aynı çıkış türünü kullanıyorsa, birden çok platform arasında çoklu hedefe daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="0b522-114">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0b522-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0b522-115">Version introduced</span></span>

<span data-ttu-id="0b522-116">.NET 5.0.1</span><span class="sxs-lookup"><span data-stu-id="0b522-116">.NET 5.0.1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0b522-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0b522-117">Recommended action</span></span>

<span data-ttu-id="0b522-118">Sizin bölüminizdeki herhangi bir eylem gerekmiyor.</span><span class="sxs-lookup"><span data-stu-id="0b522-118">No action is required in your part.</span></span> <span data-ttu-id="0b522-119">Ancak, eski davranışa dönmek istiyorsanız, `DisableWinExeOutputInference` özelliği `true` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0b522-119">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a><span data-ttu-id="0b522-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0b522-120">Affected APIs</span></span>

<span data-ttu-id="0b522-121">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="0b522-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
