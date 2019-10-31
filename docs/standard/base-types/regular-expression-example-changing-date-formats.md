---
title: 'Normal İfade Örneği: Tarih Biçimlerini Değiştirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 358e26957747073fec9dfe9eb0d404cb438afaf9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084189"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="0f646-102">Normal İfade Örneği: Tarih Biçimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0f646-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="0f646-103">Aşağıdaki kod örneği, *aa*/*gg*/*yy* biçimindeki tarihleri *gg*-*AA*-*yy*olan tarihlerle değiştirmek için <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f646-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f646-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f646-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="0f646-105">Aşağıdaki kod `MDYToDMY` yönteminin bir uygulamada nasıl çağrılabilecek olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f646-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="0f646-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f646-106">Comments</span></span>  
 <span data-ttu-id="0f646-107">Normal ifade deseninin `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="0f646-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="0f646-108">Desen</span><span class="sxs-lookup"><span data-stu-id="0f646-108">Pattern</span></span>|<span data-ttu-id="0f646-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f646-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="0f646-110">Bir sözcük sınırında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="0f646-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="0f646-111">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f646-111">Match one or two decimal digits.</span></span> <span data-ttu-id="0f646-112">Bu, yakalanan `month` grubudur.</span><span class="sxs-lookup"><span data-stu-id="0f646-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="0f646-113">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f646-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="0f646-114">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f646-114">Match one or two decimal digits.</span></span> <span data-ttu-id="0f646-115">Bu, yakalanan `day` grubudur.</span><span class="sxs-lookup"><span data-stu-id="0f646-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="0f646-116">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f646-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="0f646-117">İki ile dört ondalık basamağa eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f646-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="0f646-118">Bu, yakalanan `year` grubudur.</span><span class="sxs-lookup"><span data-stu-id="0f646-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="0f646-119">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="0f646-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="0f646-120">Model `${day}-${month}-${year}`, aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f646-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="0f646-121">Desen</span><span class="sxs-lookup"><span data-stu-id="0f646-121">Pattern</span></span>|<span data-ttu-id="0f646-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f646-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="0f646-123">`day` yakalama grubu tarafından yakalanan dizeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f646-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="0f646-124">Kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f646-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="0f646-125">`month` yakalama grubu tarafından yakalanan dizeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f646-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="0f646-126">Kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f646-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="0f646-127">`year` yakalama grubu tarafından yakalanan dizeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f646-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f646-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f646-128">See also</span></span>

- [<span data-ttu-id="0f646-129">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0f646-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
