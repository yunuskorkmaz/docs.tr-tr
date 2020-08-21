---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720218"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="ed86c-101">UNIX üzerinde UNC yollarının URI tanıması</span><span class="sxs-lookup"><span data-stu-id="ed86c-101">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="ed86c-102"><xref:System.Uri>Sınıfı artık, `//` UNIX işletim sistemlerinde evrensel adlandırma KURALı (UNC) yolları olarak iki eğik çizgi () ile başlayan dizeleri tanır.</span><span class="sxs-lookup"><span data-stu-id="ed86c-102">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="ed86c-103">Bu değişiklik, bu tür dizelerin davranışını tüm platformlarda tutarlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ed86c-103">This change makes the behavior for such strings consistent across all platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ed86c-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ed86c-104">Change description</span></span>

<span data-ttu-id="ed86c-105">.NET 'in önceki sürümlerinde, <xref:System.Uri> sınıfı iki eğik çizgi ile başlayan dizeleri tanır, örneğin, `//contoso` UNIX işletim sistemlerinde mutlak dosya yolları olarak.</span><span class="sxs-lookup"><span data-stu-id="ed86c-105">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="ed86c-106">Ancak, Windows 'ta bu tür dizeler UNC yolları olarak tanınır.</span><span class="sxs-lookup"><span data-stu-id="ed86c-106">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="ed86c-107">.NET 5,0 ' den başlayarak, <xref:System.Uri> sınıfı, UNIX dahil olmak üzere tüm platformlarda UNC yolları olarak iki eğik çizgi ile başlayan dizeleri tanır.</span><span class="sxs-lookup"><span data-stu-id="ed86c-107">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="ed86c-108">Ayrıca, Özellikler UNC semantiklerine göre davranır:</span><span class="sxs-lookup"><span data-stu-id="ed86c-108">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="ed86c-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="ed86c-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="ed86c-110">Yoldaki ters eğik çizgiler eğik çizgiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed86c-110">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="ed86c-111">Örneğin, `//first\second` olur `//first/second` .</span><span class="sxs-lookup"><span data-stu-id="ed86c-111">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="ed86c-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> karakter yüzdesi değil.</span><span class="sxs-lookup"><span data-stu-id="ed86c-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="ed86c-113">Örneğin, `//first/\uFFF0` öğesine dönüştürülmez *not* `//first/%EF%BF%B0` .</span><span class="sxs-lookup"><span data-stu-id="ed86c-113">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ed86c-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ed86c-114">Version introduced</span></span>

<span data-ttu-id="ed86c-115">5.0</span><span class="sxs-lookup"><span data-stu-id="ed86c-115">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ed86c-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ed86c-116">Recommended action</span></span>

<span data-ttu-id="ed86c-117">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ed86c-117">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="ed86c-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="ed86c-118">Category</span></span>

<span data-ttu-id="ed86c-119">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="ed86c-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ed86c-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ed86c-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
