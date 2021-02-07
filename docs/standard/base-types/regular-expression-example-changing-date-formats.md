---
description: 'Daha fazla bilgi edinin: normal Ifade örneği: tarih biçimlerini değiştirme'
title: 'Normal İfade Örneği: Tarih Biçimlerini Değiştirme'
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 4617188e958042dce9709f8baf32f5b4e2930789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702944"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="dd1d0-103">Normal İfade Örneği: Tarih Biçimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="dd1d0-103">Regular Expression Example: Changing Date Formats</span></span>

<span data-ttu-id="dd1d0-104">Aşağıdaki kod örneği, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> *AA* / *gg* / *yy* biçimindeki tarihleri *gg* - *AA* - *yy* olan tarihlerle değiştirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-104">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="dd1d0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd1d0-105">Example</span></span>  

 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="dd1d0-106">Aşağıdaki kod, `MDYToDMY` yönteminin bir uygulamada nasıl çağrılabilecek olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-106">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="dd1d0-107">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="dd1d0-107">Comments</span></span>  

 <span data-ttu-id="dd1d0-108">Normal ifade deseninin  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-108">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="dd1d0-109">Desen</span><span class="sxs-lookup"><span data-stu-id="dd1d0-109">Pattern</span></span>|<span data-ttu-id="dd1d0-110">Description</span><span class="sxs-lookup"><span data-stu-id="dd1d0-110">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="dd1d0-111">Bir sözcük sınırında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-111">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="dd1d0-112">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-112">Match one or two decimal digits.</span></span> <span data-ttu-id="dd1d0-113">Bu, `month` yakalanan gruptur.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-113">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="dd1d0-114">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-114">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="dd1d0-115">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-115">Match one or two decimal digits.</span></span> <span data-ttu-id="dd1d0-116">Bu, `day` yakalanan gruptur.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-116">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="dd1d0-117">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-117">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="dd1d0-118">İki ile dört ondalık basamağa eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-118">Match from two to four decimal digits.</span></span> <span data-ttu-id="dd1d0-119">Bu, `year` yakalanan gruptur.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-119">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="dd1d0-120">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-120">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="dd1d0-121">Bu model, `${day}-${month}-${year}` Aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-121">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="dd1d0-122">Desen</span><span class="sxs-lookup"><span data-stu-id="dd1d0-122">Pattern</span></span>|<span data-ttu-id="dd1d0-123">Description</span><span class="sxs-lookup"><span data-stu-id="dd1d0-123">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="dd1d0-124">Yakalama grubu tarafından yakalanan dizeyi ekleyin `day` .</span><span class="sxs-lookup"><span data-stu-id="dd1d0-124">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="dd1d0-125">Kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-125">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="dd1d0-126">Yakalama grubu tarafından yakalanan dizeyi ekleyin `month` .</span><span class="sxs-lookup"><span data-stu-id="dd1d0-126">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="dd1d0-127">Kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-127">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="dd1d0-128">Yakalama grubu tarafından yakalanan dizeyi ekleyin `year` .</span><span class="sxs-lookup"><span data-stu-id="dd1d0-128">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd1d0-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd1d0-129">See also</span></span>

- [<span data-ttu-id="dd1d0-130">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="dd1d0-130">.NET Regular Expressions</span></span>](regular-expressions.md)
