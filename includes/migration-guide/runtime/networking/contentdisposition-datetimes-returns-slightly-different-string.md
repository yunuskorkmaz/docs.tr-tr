---
ms.openlocfilehash: eb5c032a020799fa19cc0a8cfaabb56e01417ff4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497820"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="2065d-101">ContentDisposition DateTimes biraz farklı bir dize döndürüyor</span><span class="sxs-lookup"><span data-stu-id="2065d-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="2065d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2065d-102">Details</span></span>

<span data-ttu-id="2065d-103">Öğesinin dize temsilleri <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> , 4,6 ' dan başlayarak, her zaman iki basamaklı bir saat bileşenini temsil edecek şekilde güncelleştirilmiştir <xref:System.DateTime?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="2065d-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="2065d-104">Bu, [RFC822](https://www.ietf.org/rfc/rfc0822.txt) ve [RFC2822](https://www.ietf.org/rfc/rfc2822.txt)ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="2065d-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="2065d-105">Bu <xref:System.Net.Mime.ContentDisposition.ToString> , disposition 'nin zaman öğelerinden birinin 10:00 ' den önceki senaryolarda 4,6 ' de biraz farklı bir dize döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2065d-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="2065d-106">ContentDispositions bazen dizelere dönüştürerek serileştirildiğine, böylece tüm <xref:System.Net.Mime.ContentDisposition.ToString> işlemler, serileştirme veya GetHashCode çağrılarının gözden geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2065d-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2065d-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="2065d-107">Suggestion</span></span>

<span data-ttu-id="2065d-108">Farklı .NET Framework sürümlerinden Contentdepositions dize temsilinin doğru bir şekilde karşılaştırılacağını beklememeniz beklenmez.</span><span class="sxs-lookup"><span data-stu-id="2065d-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="2065d-109">Bir karşılaştırma yapmadan önce, mümkünse dizeleri tekrar Contentdepositions 'e dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="2065d-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="2065d-110">Name</span><span class="sxs-lookup"><span data-stu-id="2065d-110">Name</span></span>    | <span data-ttu-id="2065d-111">Değer</span><span class="sxs-lookup"><span data-stu-id="2065d-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2065d-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2065d-112">Scope</span></span>   |<span data-ttu-id="2065d-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="2065d-113">Minor</span></span>|
|<span data-ttu-id="2065d-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2065d-114">Version</span></span>|<span data-ttu-id="2065d-115">4.6</span><span class="sxs-lookup"><span data-stu-id="2065d-115">4.6</span></span>|
|<span data-ttu-id="2065d-116">Tür</span><span class="sxs-lookup"><span data-stu-id="2065d-116">Type</span></span>|<span data-ttu-id="2065d-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="2065d-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2065d-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2065d-118">Affected APIs</span></span>

- <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType>
- <xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.Mime.ContentDisposition.ToString`
- `M:System.Net.Mime.ContentDisposition.GetHashCode`

-->
