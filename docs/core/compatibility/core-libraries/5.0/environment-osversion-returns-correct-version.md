---
title: 'Son değişiklik: Environment. OSVersion doğru işletim sistemi sürümünü döndürüyor'
description: Core .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin. OSVersion, örneğin, uygulama uyumluluğu için seçilen işletim sistemi yerine işletim sisteminin gerçek sürümünü döndürür.
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761723"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="aeb81-103">Environment. OSVersion doğru işletim sistemi sürümünü döndürür</span><span class="sxs-lookup"><span data-stu-id="aeb81-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="aeb81-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> uygulama uyumluluğu için seçilen işletim sistemi (örneğin,) yerine, işletim sisteminin gerçek sürümünü (OS) döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb81-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="aeb81-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="aeb81-105">Change description</span></span>

<span data-ttu-id="aeb81-106">Önceki .NET sürümlerinde, <xref:System.Environment.OSVersion?displayProperty=nameWithType> bir uygulama Windows Uyumluluk modu altında çalıştığında hatalı olabilecek bir işletim sistemi sürümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb81-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="aeb81-107">Daha fazla bilgi için bkz. [Getversionexa işlev açıklamaları](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="aeb81-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="aeb81-108">.NET 5,0 ' den başlayarak, <xref:System.Environment.OSVersion?displayProperty=nameWithType> işletim sisteminin gerçek sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb81-108">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="aeb81-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="aeb81-109">Reason for change</span></span>

<span data-ttu-id="aeb81-110">Bu özelliğin kullanıcıları, işletim sisteminin gerçek sürümünü döndürmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="aeb81-110">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="aeb81-111">.NET uygulamalarının çoğu uygulama bildiriminde desteklenen sürümlerini belirtmemektedir ve bu nedenle DotNet ana bilgisayardan desteklenen varsayılan sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="aeb81-111">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="aeb81-112">Sonuç olarak, uyumluluk dolgusu çalışan uygulama için nadiren anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="aeb81-112">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="aeb81-113">Windows yeni bir sürüm yayımlarsa ve daha eski bir DotNet Konağı hala kullanımda olduğunda, bu uygulamalar yanlış bir işletim sistemi sürümü alabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb81-113">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="aeb81-114">Gerçek sürümü döndürmek, geliştiricilerin bu API 'nin beklentileri ile daha fazla satır içidir.</span><span class="sxs-lookup"><span data-stu-id="aeb81-114">Returning the actual version is more inline with developers' expectations of this API.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="aeb81-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="aeb81-115">Version introduced</span></span>

<span data-ttu-id="aeb81-116">5.0</span><span class="sxs-lookup"><span data-stu-id="aeb81-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="aeb81-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="aeb81-117">Recommended action</span></span>

<span data-ttu-id="aeb81-118">İstediğiniz şekilde davrandığından emin olmak için tarafından kullanılan tüm kodları gözden geçirin ve test <xref:System.Environment.OSVersion?displayProperty=nameWithType> edin.</span><span class="sxs-lookup"><span data-stu-id="aeb81-118">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="aeb81-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="aeb81-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
