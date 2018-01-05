---
title: "Normal İfade Örneği: Tarih Biçimlerini Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 93c526e87f7aba650cce397962c7262b6fd2f085
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="435bb-102">Normal İfade Örneği: Tarih Biçimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="435bb-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="435bb-103">Aşağıdaki kod örneğinde <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> formu tarihleri değiştirmek için yöntemi *mm*/*GG*/*yy* ile tarihleri Formun *GG*-*mm*-*yy*.</span><span class="sxs-lookup"><span data-stu-id="435bb-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="435bb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="435bb-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="435bb-105">Aşağıdaki kodda gösterildiği nasıl `MDYToDMY` bir uygulamada yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="435bb-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="435bb-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="435bb-106">Comments</span></span>  
 <span data-ttu-id="435bb-107">Normal ifade deseni `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="435bb-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="435bb-108">Desen</span><span class="sxs-lookup"><span data-stu-id="435bb-108">Pattern</span></span>|<span data-ttu-id="435bb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="435bb-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="435bb-110">Bir sözcük sınırında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="435bb-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="435bb-111">Bir veya iki ondalık basamak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="435bb-111">Match one or two decimal digits.</span></span> <span data-ttu-id="435bb-112">Bu `month` yakalanan grubu.</span><span class="sxs-lookup"><span data-stu-id="435bb-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="435bb-113">Eğik çizgi işareti eşleşir.</span><span class="sxs-lookup"><span data-stu-id="435bb-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="435bb-114">Bir veya iki ondalık basamak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="435bb-114">Match one or two decimal digits.</span></span> <span data-ttu-id="435bb-115">Bu `day` yakalanan grubu.</span><span class="sxs-lookup"><span data-stu-id="435bb-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="435bb-116">Eğik çizgi işareti eşleşir.</span><span class="sxs-lookup"><span data-stu-id="435bb-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="435bb-117">İki dört ondalık basamak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="435bb-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="435bb-118">Bu `year` yakalanan grubu.</span><span class="sxs-lookup"><span data-stu-id="435bb-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="435bb-119">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="435bb-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="435bb-120">Desen `${day}-${month}-${year}` aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="435bb-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="435bb-121">Desen</span><span class="sxs-lookup"><span data-stu-id="435bb-121">Pattern</span></span>|<span data-ttu-id="435bb-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="435bb-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="435bb-123">Tarafından yakalanan dizesi eklemek `day` Grup yakalama.</span><span class="sxs-lookup"><span data-stu-id="435bb-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="435bb-124">Bir tire ekleyin.</span><span class="sxs-lookup"><span data-stu-id="435bb-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="435bb-125">Tarafından yakalanan dizesi eklemek `month` Grup yakalama.</span><span class="sxs-lookup"><span data-stu-id="435bb-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="435bb-126">Bir tire ekleyin.</span><span class="sxs-lookup"><span data-stu-id="435bb-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="435bb-127">Tarafından yakalanan dizesi eklemek `year` Grup yakalama.</span><span class="sxs-lookup"><span data-stu-id="435bb-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="435bb-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="435bb-128">See Also</span></span>  
 [<span data-ttu-id="435bb-129">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="435bb-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
