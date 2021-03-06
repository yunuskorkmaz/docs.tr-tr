---
title: "Son değişiklik: System. Security. Cryptography API 'Leri Blazor WebAssembly üzerinde desteklenmiyor"
description: Şifreleme API 'Lerinin bir tarayıcıda çalıştırıldığında bir özel durum oluşturması durumunda .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 09/16/2020
ms.openlocfilehash: ecbdda4c04642af6b1737e888491eb6565ba7479
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256887"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a><span data-ttu-id="bbc54-103">System. Security. Cryptography API 'Leri Blazor WebAssembly üzerinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="bbc54-103">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>

<span data-ttu-id="bbc54-104"><xref:System.Security.Cryptography> API 'Ler <xref:System.PlatformNotSupportedException> bir tarayıcıda çalıştırıldığında bir çalışma zamanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbc54-104"><xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> at run time when run on a browser.</span></span>

## <a name="change-description"></a><span data-ttu-id="bbc54-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="bbc54-105">Change description</span></span>

<span data-ttu-id="bbc54-106">Önceki .NET sürümlerinde API 'lerin çoğu <xref:System.Security.Cryptography> Blazor WebAssembly uygulamalarında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bbc54-106">In previous .NET versions, most of the <xref:System.Security.Cryptography> APIs aren't available to Blazor WebAssembly apps.</span></span> <span data-ttu-id="bbc54-107">.NET 5 ' den başlayarak, Blazor WebAssembly Apps tam .NET 5 API Surface alanını hedeflemelidir, ancak tüm .NET 5 API 'Leri tarayıcı korumalı alan kısıtlamaları nedeniyle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="bbc54-107">Starting in .NET 5, Blazor WebAssembly apps target the full .NET 5 API surface area, however, not all .NET 5 APIs are supported due to browser sandbox constraints.</span></span> <span data-ttu-id="bbc54-108">.NET 5 ve sonraki sürümlerinde, desteklenmeyen <xref:System.Security.Cryptography> API 'Ler <xref:System.PlatformNotSupportedException> WebAssembly üzerinde çalışırken bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbc54-108">In .NET 5 and later versions, the unsupported <xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> when running on WebAssembly.</span></span>

> [!TIP]
> <span data-ttu-id="bbc54-109">[Platform uyumluluk Çözümleyicisi](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) , tarayıcı platformunu destekleyen bir proje oluşturduğunuzda etkilenen API 'lere yapılan tüm çağrıları işaret eder.</span><span class="sxs-lookup"><span data-stu-id="bbc54-109">The [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) will flag any calls to the affected APIs when you build a project that supports the browser platform.</span></span> <span data-ttu-id="bbc54-110">Bu çözümleyici, .NET 5 ve sonraki uygulamalarda varsayılan olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="bbc54-110">This analyzer runs by default in .NET 5 and later apps.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bbc54-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="bbc54-111">Reason for change</span></span>

<span data-ttu-id="bbc54-112">Microsoft, OpenSSL 'i Blazor WebAssembly yapılandırmasına bir bağımlılık olarak teslim edemiyor.</span><span class="sxs-lookup"><span data-stu-id="bbc54-112">Microsoft is unable to ship OpenSSL as a dependency in the Blazor WebAssembly configuration.</span></span> <span data-ttu-id="bbc54-113">Tarayıcının API 'siyle tümleştirmeye çalışarak bu sorunu geçici olarak çözmek için denedik `SubtleCrypto` .</span><span class="sxs-lookup"><span data-stu-id="bbc54-113">We attempted to work around this by trying to integrate with the browser's `SubtleCrypto` API.</span></span> <span data-ttu-id="bbc54-114">Ne yazık ki, tümleştirme çok zor olan önemli API değişiklikleri gerektirdi.</span><span class="sxs-lookup"><span data-stu-id="bbc54-114">Unfortunately, it required significant API changes that made it too hard to integrate.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bbc54-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="bbc54-115">Version introduced</span></span>

<span data-ttu-id="bbc54-116">5.0</span><span class="sxs-lookup"><span data-stu-id="bbc54-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bbc54-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="bbc54-117">Recommended action</span></span>

<span data-ttu-id="bbc54-118">Şu anda önerecek iyi bir geçici çözüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="bbc54-118">There are no good workarounds to suggest at this time.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bbc54-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bbc54-119">Affected APIs</span></span>

<span data-ttu-id="bbc54-120"><xref:System.Security.Cryptography?displayProperty=fullName>Aşağıdakiler hariç tüm API 'ler:</span><span class="sxs-lookup"><span data-stu-id="bbc54-120">All <xref:System.Security.Cryptography?displayProperty=fullName> APIs except the following:</span></span>

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->
