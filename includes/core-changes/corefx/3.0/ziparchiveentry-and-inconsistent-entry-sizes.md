---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568243"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="5cbe3-101">ZipArchiveEntry artık tutarsız giriş boyutları ile arşivleri işler</span><span class="sxs-lookup"><span data-stu-id="5cbe3-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="5cbe3-102">Zip arşivleri, hem sıkıştırılmış boyutu hem de sıkıştırılmamış boyutu merkez dizini ve yerel üstbilgide listeler.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="5cbe3-103">Giriş verilerinin kendisi de boyutunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="5cbe3-104">.NET Core 2.2 ve önceki sürümlerinde, bu değerler tutarlılık açısından hiçbir zaman denetlenmedi.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="5cbe3-105">.NET Core 3.0 ile başlayarak, şimdi vardır.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5cbe3-106">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="5cbe3-106">Change description</span></span>

<span data-ttu-id="5cbe3-107">.NET Core 2.2 ve <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> önceki sürümlerinde, yerel üstbilgi zip dosyasının merkezi üstbilgiyle aynı fikirde olmasa bile başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="5cbe3-108">Veri, uzunluğu merkezi dizinde/yerel üstbilgide listelenen sıkıştırılmamış dosya boyutunu aşsa bile, sıkıştırılmış akışın sonuna kadar sıkıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="5cbe3-109">.NET Core 3.0 ile <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> başlayarak, yöntem yerel üstbilgi ve merkezi üstbilginin bir girişin sıkıştırılmış ve sıkıştırılmamış boyutları üzerinde anlaştığını denetler.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="5cbe3-110">Bunu yapmazlarsa, yöntem, arşivin yerel üstbilgi ve/veya zip dosyasının merkezi diziniyle aynı fikirde olmayan veri tanımlayıcı listesi boyutları varsa bir <xref:System.IO.InvalidDataException> hata yapar.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="5cbe3-111">Bir giriş okurken, sıkıştırılmış veriler üstbilgide listelenen sıkıştırılmamış dosya boyutuna kesilir.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="5cbe3-112">Bu değişiklik, bir verinin <xref:System.IO.Compression.ZipArchiveEntry> boyutunu doğru bir şekilde temsil etmesini ve yalnızca bu miktarda verinin okunmasını sağlamak için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5cbe3-113">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="5cbe3-113">Version introduced</span></span>

<span data-ttu-id="5cbe3-114">3,0</span><span class="sxs-lookup"><span data-stu-id="5cbe3-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5cbe3-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5cbe3-115">Recommended action</span></span>

<span data-ttu-id="5cbe3-116">Bu sorunları sergileyen herhangi bir zip arşivini yeniden paketleyin.</span><span class="sxs-lookup"><span data-stu-id="5cbe3-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="5cbe3-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="5cbe3-117">Category</span></span>

<span data-ttu-id="5cbe3-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="5cbe3-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5cbe3-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5cbe3-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
