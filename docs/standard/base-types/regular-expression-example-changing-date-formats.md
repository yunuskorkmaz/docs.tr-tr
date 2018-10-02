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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c26608115a22a5402d671c5f5e51c75442a0a5
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862139"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="3ea48-102">Normal İfade Örneği: Tarih Biçimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3ea48-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="3ea48-103">Aşağıdaki kod örneğinde <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> formu tarihleri yönteminin *mm*/*GG*/*yy* ile tarihleri Formun *GG*-*mm*-*yy*.</span><span class="sxs-lookup"><span data-stu-id="3ea48-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ea48-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ea48-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="3ea48-105">Aşağıdaki kodda gösterildiği nasıl `MDYToDMY` yöntemi, uygulamada çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ea48-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="3ea48-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ea48-106">Comments</span></span>  
 <span data-ttu-id="3ea48-107">Normal ifade deseni `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="3ea48-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="3ea48-108">Desen</span><span class="sxs-lookup"><span data-stu-id="3ea48-108">Pattern</span></span>|<span data-ttu-id="3ea48-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ea48-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="3ea48-110">Bir sözcük sınırında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="3ea48-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="3ea48-111">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="3ea48-111">Match one or two decimal digits.</span></span> <span data-ttu-id="3ea48-112">Bu `month` yakalanan grubu.</span><span class="sxs-lookup"><span data-stu-id="3ea48-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="3ea48-113">Eğik çizgi işareti eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="3ea48-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="3ea48-114">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="3ea48-114">Match one or two decimal digits.</span></span> <span data-ttu-id="3ea48-115">Bu `day` yakalanan grubu.</span><span class="sxs-lookup"><span data-stu-id="3ea48-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="3ea48-116">Eğik çizgi işareti eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="3ea48-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="3ea48-117">Dört ondalık basamak için ikisinden eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="3ea48-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="3ea48-118">Bu `year` yakalanan grubu.</span><span class="sxs-lookup"><span data-stu-id="3ea48-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="3ea48-119">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="3ea48-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="3ea48-120">Desen `${day}-${month}-${year}` değiştirme dizesi aşağıdaki tabloda gösterildiği gibi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ea48-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="3ea48-121">Desen</span><span class="sxs-lookup"><span data-stu-id="3ea48-121">Pattern</span></span>|<span data-ttu-id="3ea48-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ea48-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="3ea48-123">Tarafından yakalanan dizesi eklemek `day` yakalama grubu.</span><span class="sxs-lookup"><span data-stu-id="3ea48-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="3ea48-124">Bir kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ea48-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="3ea48-125">Tarafından yakalanan dizesi eklemek `month` yakalama grubu.</span><span class="sxs-lookup"><span data-stu-id="3ea48-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="3ea48-126">Bir kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ea48-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="3ea48-127">Tarafından yakalanan dizesi eklemek `year` yakalama grubu.</span><span class="sxs-lookup"><span data-stu-id="3ea48-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ea48-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ea48-128">See also</span></span>

- [<span data-ttu-id="3ea48-129">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="3ea48-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
