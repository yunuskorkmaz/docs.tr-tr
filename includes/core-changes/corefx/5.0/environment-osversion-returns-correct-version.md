---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558197"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="c0dbb-101">Environment. OSVersion doğru işletim sistemi sürümünü döndürür</span><span class="sxs-lookup"><span data-stu-id="c0dbb-101">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="c0dbb-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> uygulama uyumluluğu için seçilen işletim sistemi (örneğin,) yerine, işletim sisteminin gerçek sürümünü (OS) döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c0dbb-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c0dbb-103">Change description</span></span>

<span data-ttu-id="c0dbb-104">Önceki .NET sürümlerinde, <xref:System.Environment.OSVersion?displayProperty=nameWithType> bir uygulama Windows Uyumluluk modu altında çalıştığında hatalı olabilecek bir işletim sistemi sürümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-104">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="c0dbb-105">Daha fazla bilgi için bkz. [Getversionexa işlev açıklamaları](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="c0dbb-105">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="c0dbb-106">.NET 5,0 ' den başlayarak, <xref:System.Environment.OSVersion?displayProperty=nameWithType> işletim sisteminin gerçek sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-106">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c0dbb-107">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c0dbb-107">Reason for change</span></span>

<span data-ttu-id="c0dbb-108">Bu özelliğin kullanıcıları, işletim sisteminin gerçek sürümünü döndürmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-108">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="c0dbb-109">.NET uygulamalarının çoğu uygulama bildiriminde desteklenen sürümlerini belirtmemektedir ve bu nedenle DotNet ana bilgisayardan desteklenen varsayılan sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-109">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="c0dbb-110">Sonuç olarak, uyumluluk dolgusu çalışan uygulama için nadiren anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-110">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="c0dbb-111">Windows yeni bir sürüm yayımlarsa ve daha eski bir DotNet Konağı hala kullanımda olduğunda, bu uygulamalar yanlış bir işletim sistemi sürümü alabilir.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-111">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="c0dbb-112">Gerçek sürümü döndürmek, geliştiricilerin bu API 'nin beklentileri ile daha fazla satır içidir.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-112">Returning the actual version is more inline with developers' expectations of this API.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c0dbb-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c0dbb-113">Version introduced</span></span>

<span data-ttu-id="c0dbb-114">5.0</span><span class="sxs-lookup"><span data-stu-id="c0dbb-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c0dbb-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c0dbb-115">Recommended action</span></span>

<span data-ttu-id="c0dbb-116">İstediğiniz şekilde davrandığından emin olmak için tarafından kullanılan tüm kodları gözden geçirin ve test <xref:System.Environment.OSVersion?displayProperty=nameWithType> edin.</span><span class="sxs-lookup"><span data-stu-id="c0dbb-116">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

#### <a name="category"></a><span data-ttu-id="c0dbb-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="c0dbb-117">Category</span></span>

<span data-ttu-id="c0dbb-118">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="c0dbb-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c0dbb-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c0dbb-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->
