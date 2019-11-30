---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568243"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="991b3-101">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="991b3-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="991b3-102">ZIP arşivi, merkezi dizinde ve yerel üstbilgide Sıkıştırılmış boyut ve sıkıştırılmamış boyut listesini de listeler.</span><span class="sxs-lookup"><span data-stu-id="991b3-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="991b3-103">Giriş verilerinin kendisi de boyutunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="991b3-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="991b3-104">.NET Core 2,2 ve önceki sürümlerinde, bu değerler hiçbir şekilde tutarlılık denetimi yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="991b3-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="991b3-105">.NET Core 3,0 ' den itibaren artık kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="991b3-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="991b3-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="991b3-106">Change description</span></span>

<span data-ttu-id="991b3-107">.NET Core 2,2 ve önceki sürümlerde <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>, yerel üst bilgi ZIP dosyasının orta üst bilgisiyle kabul etmese bile başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="991b3-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="991b3-108">Verilerin uzunluğu, merkezi Dizin/yerel üst bilgisinde listelenen sıkıştırılmamış dosya boyutunu aşsa bile, sıkıştırılan akışın sonuna ulaşılana kadar veriler açılır.</span><span class="sxs-lookup"><span data-stu-id="991b3-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="991b3-109"><xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> yöntemi, .NET Core 3,0 ile başlayarak, bir girdinin sıkıştırılmış ve sıkıştırılmamış boyutları üzerinde, yerel üst bilgi ve orta üst bilgi kullanımını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="991b3-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="991b3-110">Aksi takdirde, arşiv 'in yerel üstbilgisi ve/veya ZIP dosyasının merkezi diziniyle kabul eterdikleri veri tanımlayıcısı listesi boyutları yoksa Yöntem bir <xref:System.IO.InvalidDataException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="991b3-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="991b3-111">Bir girişi okurken, sıkıştırması açılmış veriler üst bilgide listelenen sıkıştırılmamış dosya boyutuna kesilir.</span><span class="sxs-lookup"><span data-stu-id="991b3-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="991b3-112">Bu değişiklik, bir <xref:System.IO.Compression.ZipArchiveEntry> verilerin boyutunu doğru bir şekilde temsil ettiğinden ve yalnızca o miktarda veri okunduğunuzdan emin olmak için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="991b3-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="991b3-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="991b3-113">Version introduced</span></span>

<span data-ttu-id="991b3-114">3.0</span><span class="sxs-lookup"><span data-stu-id="991b3-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="991b3-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="991b3-115">Recommended action</span></span>

<span data-ttu-id="991b3-116">Bu sorunları gösteren herhangi bir ZIP arşivini yeniden paketleyin.</span><span class="sxs-lookup"><span data-stu-id="991b3-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="991b3-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="991b3-117">Category</span></span>

<span data-ttu-id="991b3-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="991b3-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="991b3-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="991b3-119">Affected APIs</span></span>

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
