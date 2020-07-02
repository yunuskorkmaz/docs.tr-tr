---
ms.openlocfilehash: c103dff320ae30d02c12ea5c585a47b589da8237
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621423"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="38c2e-101">ContentDisposition DateTimes biraz farklı bir dize döndürüyor</span><span class="sxs-lookup"><span data-stu-id="38c2e-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="38c2e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="38c2e-102">Details</span></span>

<span data-ttu-id="38c2e-103">Öğesinin dize temsilleri <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> , 4,6 ' dan başlayarak, her zaman iki basamaklı bir saat bileşenini temsil edecek şekilde güncelleştirilmiştir <xref:System.DateTime?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="38c2e-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="38c2e-104">Bu, [RFC822](https://www.ietf.org/rfc/rfc0822.txt) ve [RFC2822](https://www.ietf.org/rfc/rfc2822.txt)ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="38c2e-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="38c2e-105">Bu <xref:System.Net.Mime.ContentDisposition.ToString> , disposition 'nin zaman öğelerinden birinin 10:00 ' den önceki senaryolarda 4,6 ' de biraz farklı bir dize döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="38c2e-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="38c2e-106">ContentDispositions bazen dizelere dönüştürerek serileştirildiğine, böylece tüm <xref:System.Net.Mime.ContentDisposition.ToString> işlemler, serileştirme veya GetHashCode çağrılarının gözden geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="38c2e-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="38c2e-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="38c2e-107">Suggestion</span></span>

<span data-ttu-id="38c2e-108">Farklı .NET Framework sürümlerinden Contentdepositions dize temsilinin doğru bir şekilde karşılaştırılacağını beklememeniz beklenmez.</span><span class="sxs-lookup"><span data-stu-id="38c2e-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="38c2e-109">Bir karşılaştırma yapmadan önce, mümkünse dizeleri tekrar Contentdepositions 'e dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="38c2e-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="38c2e-110">Name</span><span class="sxs-lookup"><span data-stu-id="38c2e-110">Name</span></span>    | <span data-ttu-id="38c2e-111">Değer</span><span class="sxs-lookup"><span data-stu-id="38c2e-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="38c2e-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="38c2e-112">Scope</span></span>   |<span data-ttu-id="38c2e-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="38c2e-113">Minor</span></span>|
|<span data-ttu-id="38c2e-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="38c2e-114">Version</span></span>|<span data-ttu-id="38c2e-115">4.6</span><span class="sxs-lookup"><span data-stu-id="38c2e-115">4.6</span></span>|
|<span data-ttu-id="38c2e-116">Tür</span><span class="sxs-lookup"><span data-stu-id="38c2e-116">Type</span></span>|<span data-ttu-id="38c2e-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="38c2e-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38c2e-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="38c2e-118">Affected APIs</span></span>

-<xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
