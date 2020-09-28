---
ms.openlocfilehash: 6c2aff4abf558307d599ff7533c82286e037bc71
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406160"
---
### <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a><span data-ttu-id="43cc4-101">System. Security. Cryptography API 'Leri Blazor WebAssembly üzerinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="43cc4-101">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>

<span data-ttu-id="43cc4-102"><xref:System.Security.Cryptography> API 'Ler <xref:System.PlatformNotSupportedException> bir tarayıcıda çalıştırıldığında bir çalışma zamanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43cc4-102"><xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> at run time when run on a browser.</span></span>

#### <a name="change-description"></a><span data-ttu-id="43cc4-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="43cc4-103">Change description</span></span>

<span data-ttu-id="43cc4-104">Önceki .NET sürümlerinde API 'lerin çoğu <xref:System.Security.Cryptography> Blazor WebAssembly uygulamalarında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="43cc4-104">In previous .NET versions, most of the <xref:System.Security.Cryptography> APIs aren't available to Blazor WebAssembly apps.</span></span> <span data-ttu-id="43cc4-105">.NET 5,0 ' den başlayarak, Blazor WebAssembly Apps tam .NET 5 API Surface alanını hedeflemelidir, ancak tüm .NET 5 API 'Leri tarayıcı korumalı alan kısıtlamaları nedeniyle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="43cc4-105">Starting in .NET 5.0, Blazor WebAssembly apps target the full .NET 5 API surface area, however, not all .NET 5 APIs are supported due to browser sandbox constraints.</span></span> <span data-ttu-id="43cc4-106">.NET 5,0 ve sonraki sürümlerinde, desteklenmeyen <xref:System.Security.Cryptography> API 'Ler <xref:System.PlatformNotSupportedException> WebAssembly üzerinde çalışırken bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43cc4-106">In .NET 5.0 and later versions, the unsupported <xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> when running on WebAssembly.</span></span>

> [!TIP]
> <span data-ttu-id="43cc4-107">[Platform uyumluluk Çözümleyicisi](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) , tarayıcı platformunu destekleyen bir proje oluşturduğunuzda etkilenen API 'lere yapılan tüm çağrıları işaret eder.</span><span class="sxs-lookup"><span data-stu-id="43cc4-107">The [Platform compatibility analyzer](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) will flag any calls to the affected APIs when you build a project that supports the browser platform.</span></span> <span data-ttu-id="43cc4-108">Bu çözümleyici, .NET 5,0 ve sonraki uygulamalarda varsayılan olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="43cc4-108">This analyzer runs by default in .NET 5.0 and later apps.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="43cc4-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="43cc4-109">Reason for change</span></span>

<span data-ttu-id="43cc4-110">Microsoft, OpenSSL 'i Blazor WebAssembly yapılandırmasına bir bağımlılık olarak teslim edemiyor.</span><span class="sxs-lookup"><span data-stu-id="43cc4-110">Microsoft is unable to ship OpenSSL as a dependency in the Blazor WebAssembly configuration.</span></span> <span data-ttu-id="43cc4-111">Tarayıcının API 'siyle tümleştirmeye çalışarak bu sorunu geçici olarak çözmek için denedik `SubtleCrypto` .</span><span class="sxs-lookup"><span data-stu-id="43cc4-111">We attempted to work around this by trying to integrate with the browser's `SubtleCrypto` API.</span></span> <span data-ttu-id="43cc4-112">Ne yazık ki, tümleştirme çok zor olan önemli API değişiklikleri gerektirdi.</span><span class="sxs-lookup"><span data-stu-id="43cc4-112">Unfortunately, it required significant API changes that made it too hard to integrate.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="43cc4-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="43cc4-113">Version introduced</span></span>

<span data-ttu-id="43cc4-114">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="43cc4-114">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="43cc4-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="43cc4-115">Recommended action</span></span>

<span data-ttu-id="43cc4-116">Şu anda önerecek iyi bir geçici çözüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="43cc4-116">There are no good workarounds to suggest at this time.</span></span>

#### <a name="category"></a><span data-ttu-id="43cc4-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="43cc4-117">Category</span></span>

- <span data-ttu-id="43cc4-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="43cc4-118">ASP.NET Core</span></span>
- <span data-ttu-id="43cc4-119">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="43cc4-119">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="43cc4-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="43cc4-120">Affected APIs</span></span>

<span data-ttu-id="43cc4-121"><xref:System.Security.Cryptography?displayProperty=fullName>Aşağıdakiler hariç tüm API 'ler:</span><span class="sxs-lookup"><span data-stu-id="43cc4-121">All <xref:System.Security.Cryptography?displayProperty=fullName> APIs except the following:</span></span>

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

#### Affected APIs

- `T:System.Security.Cryptography`

-->
