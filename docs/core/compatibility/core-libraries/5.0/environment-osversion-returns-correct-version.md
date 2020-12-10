---
title: 'Son değişiklik: Environment. OSVersion doğru işletim sistemi sürümünü döndürüyor'
description: Core .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin. OSVersion, örneğin, uygulama uyumluluğu için seçilen işletim sistemi yerine işletim sisteminin gerçek sürümünü döndürür.
ms.date: 11/01/2020
ms.openlocfilehash: c810d9a7a028a0c60c30d69e78a9b9c695d933ef
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009527"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="30dad-103">Environment. OSVersion doğru işletim sistemi sürümünü döndürür</span><span class="sxs-lookup"><span data-stu-id="30dad-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="30dad-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> uygulama uyumluluğu için seçilen işletim sistemi (örneğin,) yerine, işletim sisteminin gerçek sürümünü (OS) döndürür.</span><span class="sxs-lookup"><span data-stu-id="30dad-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="30dad-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="30dad-105">Change description</span></span>

<span data-ttu-id="30dad-106">Önceki .NET sürümlerinde, <xref:System.Environment.OSVersion?displayProperty=nameWithType> bir uygulama Windows Uyumluluk modu altında çalıştığında hatalı olabilecek bir işletim sistemi sürümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="30dad-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="30dad-107">Daha fazla bilgi için bkz. [Getversionexa işlev açıklamaları](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="30dad-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span> <span data-ttu-id="30dad-108">MacOS 'ta <xref:System.Environment.OSVersion?displayProperty=nameWithType> temeldeki Darwin çekirdek sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="30dad-108">On macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the underlying Darwin kernel version.</span></span>

<span data-ttu-id="30dad-109">.NET 5,0 ' den itibaren, <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows ve macOS için işletim sisteminin gerçek sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="30dad-109">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system for Windows and macOS.</span></span>

<span data-ttu-id="30dad-110">Aşağıdaki tabloda davranış farkı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="30dad-110">The following table shows the difference in behavior.</span></span>

|  | <span data-ttu-id="30dad-111">Önceki .NET sürümleri</span><span class="sxs-lookup"><span data-stu-id="30dad-111">Previous .NET versions</span></span> | <span data-ttu-id="30dad-112">.NET 5 +</span><span class="sxs-lookup"><span data-stu-id="30dad-112">.NET 5+</span></span> |
|--|------------------------|---------|
| <span data-ttu-id="30dad-113">Windows</span><span class="sxs-lookup"><span data-stu-id="30dad-113">Windows</span></span> | <span data-ttu-id="30dad-114">6.2.9200.0</span><span class="sxs-lookup"><span data-stu-id="30dad-114">6.2.9200.0</span></span> | <span data-ttu-id="30dad-115">10.0.19042.0</span><span class="sxs-lookup"><span data-stu-id="30dad-115">10.0.19042.0</span></span> |
| <span data-ttu-id="30dad-116">macOS</span><span class="sxs-lookup"><span data-stu-id="30dad-116">macOS</span></span> | <span data-ttu-id="30dad-117">19.6.0.0</span><span class="sxs-lookup"><span data-stu-id="30dad-117">19.6.0.0</span></span> | <span data-ttu-id="30dad-118">10.15.7</span><span class="sxs-lookup"><span data-stu-id="30dad-118">10.15.7</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="30dad-119">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="30dad-119">Reason for change</span></span>

<span data-ttu-id="30dad-120">Bu özelliğin kullanıcıları, işletim sisteminin gerçek sürümünü döndürmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="30dad-120">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="30dad-121">.NET uygulamalarının çoğu uygulama bildiriminde desteklenen sürümlerini belirtmemektedir ve bu nedenle DotNet ana bilgisayardan desteklenen varsayılan sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="30dad-121">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="30dad-122">Sonuç olarak, uyumluluk dolgusu çalışan uygulama için nadiren anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="30dad-122">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="30dad-123">Windows yeni bir sürüm yayımlarsa ve daha eski bir DotNet Konağı hala kullanımda olduğunda, bu uygulamalar yanlış bir işletim sistemi sürümü alabilir.</span><span class="sxs-lookup"><span data-stu-id="30dad-123">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="30dad-124">Gerçek sürümü döndürmek, geliştiricilerin bu API 'nin beklentileri ile daha fazla satır içidir.</span><span class="sxs-lookup"><span data-stu-id="30dad-124">Returning the actual version is more inline with developers' expectations of this API.</span></span>

<span data-ttu-id="30dad-125"><xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> .NET 5,0 ' e giriş ile <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows ve MacOS için tutarlı olacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="30dad-125">With the introduction of <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>, and <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> was changed to be consistent for Windows and macOS.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="30dad-126">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="30dad-126">Version introduced</span></span>

<span data-ttu-id="30dad-127">5.0</span><span class="sxs-lookup"><span data-stu-id="30dad-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="30dad-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="30dad-128">Recommended action</span></span>

<span data-ttu-id="30dad-129">İstediğiniz şekilde davrandığından emin olmak için tarafından kullanılan tüm kodları gözden geçirin ve test <xref:System.Environment.OSVersion?displayProperty=nameWithType> edin.</span><span class="sxs-lookup"><span data-stu-id="30dad-129">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="30dad-130">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="30dad-130">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
