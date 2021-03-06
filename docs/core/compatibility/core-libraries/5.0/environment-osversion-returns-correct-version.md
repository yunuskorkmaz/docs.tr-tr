---
title: 'Son değişiklik: Environment. OSVersion doğru işletim sistemi sürümünü döndürüyor'
description: Core .NET kitaplıklarında .NET 5 ' ün son değişikliği hakkında bilgi edinin. OSVersion, örneğin, uygulama uyumluluğu için seçilen işletim sistemi yerine işletim sisteminin gerçek sürümünü döndürür.
ms.date: 11/01/2020
ms.openlocfilehash: 05ec886061263ea43a2d956b8ce0ecc06e2bf3ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257537"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="d6620-103">Environment. OSVersion doğru işletim sistemi sürümünü döndürür</span><span class="sxs-lookup"><span data-stu-id="d6620-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="d6620-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> uygulama uyumluluğu için seçilen işletim sistemi (örneğin,) yerine, işletim sisteminin gerçek sürümünü (OS) döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6620-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="d6620-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="d6620-105">Change description</span></span>

<span data-ttu-id="d6620-106">Önceki .NET sürümlerinde, <xref:System.Environment.OSVersion?displayProperty=nameWithType> bir uygulama Windows Uyumluluk modu altında çalıştığında hatalı olabilecek bir işletim sistemi sürümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6620-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="d6620-107">Daha fazla bilgi için bkz. [Getversionexa işlev açıklamaları](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="d6620-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span> <span data-ttu-id="d6620-108">MacOS 'ta <xref:System.Environment.OSVersion?displayProperty=nameWithType> temeldeki Darwin çekirdek sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6620-108">On macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the underlying Darwin kernel version.</span></span>

<span data-ttu-id="d6620-109">.NET 5 ' den itibaren, <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows ve macOS için işletim sisteminin gerçek sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6620-109">Starting in .NET 5, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system for Windows and macOS.</span></span>

<span data-ttu-id="d6620-110">Aşağıdaki tabloda davranış farkı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d6620-110">The following table shows the difference in behavior.</span></span>

|  | <span data-ttu-id="d6620-111">Önceki .NET sürümleri</span><span class="sxs-lookup"><span data-stu-id="d6620-111">Previous .NET versions</span></span> | <span data-ttu-id="d6620-112">.NET 5 +</span><span class="sxs-lookup"><span data-stu-id="d6620-112">.NET 5+</span></span> |
|--|------------------------|---------|
| <span data-ttu-id="d6620-113">Windows</span><span class="sxs-lookup"><span data-stu-id="d6620-113">Windows</span></span> | <span data-ttu-id="d6620-114">6.2.9200.0</span><span class="sxs-lookup"><span data-stu-id="d6620-114">6.2.9200.0</span></span> | <span data-ttu-id="d6620-115">10.0.19042.0</span><span class="sxs-lookup"><span data-stu-id="d6620-115">10.0.19042.0</span></span> |
| <span data-ttu-id="d6620-116">Mac OS</span><span class="sxs-lookup"><span data-stu-id="d6620-116">macOS</span></span> | <span data-ttu-id="d6620-117">19.6.0.0</span><span class="sxs-lookup"><span data-stu-id="d6620-117">19.6.0.0</span></span> | <span data-ttu-id="d6620-118">10.15.7</span><span class="sxs-lookup"><span data-stu-id="d6620-118">10.15.7</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="d6620-119">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d6620-119">Reason for change</span></span>

<span data-ttu-id="d6620-120">Bu özelliğin kullanıcıları, işletim sisteminin gerçek sürümünü döndürmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="d6620-120">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="d6620-121">.NET uygulamalarının çoğu uygulama bildiriminde desteklenen sürümlerini belirtmemektedir ve bu nedenle DotNet ana bilgisayardan desteklenen varsayılan sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="d6620-121">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="d6620-122">Sonuç olarak, uyumluluk dolgusu çalışan uygulama için nadiren anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="d6620-122">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="d6620-123">Windows yeni bir sürüm yayımlarsa ve daha eski bir DotNet Konağı hala kullanımda olduğunda, bu uygulamalar yanlış bir işletim sistemi sürümü alabilir.</span><span class="sxs-lookup"><span data-stu-id="d6620-123">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="d6620-124">Gerçek sürümü döndürmek, geliştiricilerin bu API 'nin beklentileri ile daha fazla satır içidir.</span><span class="sxs-lookup"><span data-stu-id="d6620-124">Returning the actual version is more inline with developers' expectations of this API.</span></span>

<span data-ttu-id="d6620-125">, <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> Ve <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> .NET 5 ' e giriş Ile <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows ve MacOS için tutarlı olacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d6620-125">With the introduction of <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>, and <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> in .NET 5, <xref:System.Environment.OSVersion?displayProperty=nameWithType> was changed to be consistent for Windows and macOS.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d6620-126">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d6620-126">Version introduced</span></span>

<span data-ttu-id="d6620-127">5.0</span><span class="sxs-lookup"><span data-stu-id="d6620-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d6620-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d6620-128">Recommended action</span></span>

<span data-ttu-id="d6620-129">İstediğiniz şekilde davrandığından emin olmak için tarafından kullanılan tüm kodları gözden geçirin ve test <xref:System.Environment.OSVersion?displayProperty=nameWithType> edin.</span><span class="sxs-lookup"><span data-stu-id="d6620-129">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d6620-130">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d6620-130">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
