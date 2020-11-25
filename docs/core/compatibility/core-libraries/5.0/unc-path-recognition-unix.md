---
title: 'Son değişiklik: UNIX üzerinde UNC yollarının URI tanıması'
description: URI sınıfının artık UNIX üzerinde UNC yolları olarak iki eğik çizgi ile başlayan dizeleri tanıdığı çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761386"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="dd91d-103">UNIX üzerinde UNC yollarının URI tanıması</span><span class="sxs-lookup"><span data-stu-id="dd91d-103">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="dd91d-104"><xref:System.Uri>Sınıfı artık, `//` UNIX işletim sistemlerinde evrensel adlandırma KURALı (UNC) yolları olarak iki eğik çizgi () ile başlayan dizeleri tanır.</span><span class="sxs-lookup"><span data-stu-id="dd91d-104">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="dd91d-105">Bu değişiklik, bu tür dizelerin davranışını tüm platformlarda tutarlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="dd91d-105">This change makes the behavior for such strings consistent across all platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="dd91d-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="dd91d-106">Change description</span></span>

<span data-ttu-id="dd91d-107">.NET 'in önceki sürümlerinde, <xref:System.Uri> sınıfı iki eğik çizgi ile başlayan dizeleri (örneğin, `//contoso` UNIX işletim sistemlerinde mutlak dosya yolları) tanır.</span><span class="sxs-lookup"><span data-stu-id="dd91d-107">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="dd91d-108">Ancak, Windows 'ta bu tür dizeler UNC yolları olarak tanınır.</span><span class="sxs-lookup"><span data-stu-id="dd91d-108">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="dd91d-109">.NET 5,0 ' den başlayarak, <xref:System.Uri> sınıfı, UNIX dahil olmak üzere tüm platformlarda UNC yolları olarak iki eğik çizgi ile başlayan dizeleri tanır.</span><span class="sxs-lookup"><span data-stu-id="dd91d-109">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="dd91d-110">Ayrıca, Özellikler UNC semantiklerine göre davranır:</span><span class="sxs-lookup"><span data-stu-id="dd91d-110">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="dd91d-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="dd91d-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="dd91d-112">Yoldaki ters eğik çizgiler eğik çizgiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd91d-112">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="dd91d-113">Örneğin, `//first\second` olur `//first/second` .</span><span class="sxs-lookup"><span data-stu-id="dd91d-113">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="dd91d-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> karakter yüzdesi değil.</span><span class="sxs-lookup"><span data-stu-id="dd91d-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="dd91d-115">Örneğin, `//first/\uFFF0` öğesine dönüştürülmez *not* `//first/%EF%BF%B0` .</span><span class="sxs-lookup"><span data-stu-id="dd91d-115">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="dd91d-116">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="dd91d-116">Version introduced</span></span>

<span data-ttu-id="dd91d-117">5.0</span><span class="sxs-lookup"><span data-stu-id="dd91d-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="dd91d-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="dd91d-118">Recommended action</span></span>

<span data-ttu-id="dd91d-119">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dd91d-119">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="dd91d-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="dd91d-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
