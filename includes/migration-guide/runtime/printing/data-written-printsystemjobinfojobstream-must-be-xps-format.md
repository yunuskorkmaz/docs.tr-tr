---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620645"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="57631-101">PrintSystemJobInfo. JobStream 'e yazılan veriler XPS biçiminde olmalıdır</span><span class="sxs-lookup"><span data-stu-id="57631-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

#### <a name="details"></a><span data-ttu-id="57631-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="57631-102">Details</span></span>

<span data-ttu-id="57631-103"><xref:System.Printing.PrintSystemJobInfo.JobStream>Özelliği, bir yazdırma işinin akışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="57631-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="57631-104">Kullanıcı, ham verileri, bu akışa yazarak temel işletim sistemi yazdırma bileşenlerine gönderebilir. Windows 8 ' de ve Windows işletim sisteminin sonraki sürümlerinde 4,5 .NET Framework başlayarak, bu akışa yazılan verilerin bir paket akışı olarak XPS biçiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="57631-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="57631-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="57631-105">Suggestion</span></span>

<span data-ttu-id="57631-106">Yazdırma içeriğini çıkarmak için aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="57631-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="57631-107"><xref:System.Windows.Xps.XpsDocumentWriter>Yazdırma içeriğini çıkarmak için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="57631-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="57631-108">Önerilen seçenek budur.</span><span class="sxs-lookup"><span data-stu-id="57631-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="57631-109">Özelliği tarafından döndürülen akışa gönderilen verilerin <xref:System.Printing.PrintSystemJobInfo.JobStream> bir paket akışı olarak XPS biçiminde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="57631-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>

| <span data-ttu-id="57631-110">Name</span><span class="sxs-lookup"><span data-stu-id="57631-110">Name</span></span>    | <span data-ttu-id="57631-111">Değer</span><span class="sxs-lookup"><span data-stu-id="57631-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="57631-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="57631-112">Scope</span></span>   |<span data-ttu-id="57631-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="57631-113">Minor</span></span>|
|<span data-ttu-id="57631-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="57631-114">Version</span></span>|<span data-ttu-id="57631-115">4,5</span><span class="sxs-lookup"><span data-stu-id="57631-115">4.5</span></span>|
|<span data-ttu-id="57631-116">Tür</span><span class="sxs-lookup"><span data-stu-id="57631-116">Type</span></span>|<span data-ttu-id="57631-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="57631-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="57631-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="57631-118">Affected APIs</span></span>

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
