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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084189"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="75a38-102">Normal İfade Örneği: Tarih Biçimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="75a38-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="75a38-103">Aşağıdaki kod örneği, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> *dd*-*mm*-yy formuna sahip tarihler ile *mm*/*dd*/*yy* formuna sahip tarihleri değiştirmek için yöntemi kullanır.*yy*</span><span class="sxs-lookup"><span data-stu-id="75a38-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a38-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="75a38-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="75a38-105">Aşağıdaki kod, yöntemin `MDYToDMY` bir uygulamada nasıl çağrılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="75a38-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="75a38-106">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="75a38-106">Comments</span></span>  
 <span data-ttu-id="75a38-107">Normal ifade `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="75a38-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="75a38-108">Desen</span><span class="sxs-lookup"><span data-stu-id="75a38-108">Pattern</span></span>|<span data-ttu-id="75a38-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75a38-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="75a38-110">Bir sözcük sınırında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="75a38-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="75a38-111">Bir veya iki ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="75a38-111">Match one or two decimal digits.</span></span> <span data-ttu-id="75a38-112">Bu `month` yakalanan grup.</span><span class="sxs-lookup"><span data-stu-id="75a38-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="75a38-113">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="75a38-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="75a38-114">Bir veya iki ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="75a38-114">Match one or two decimal digits.</span></span> <span data-ttu-id="75a38-115">Bu `day` yakalanan grup.</span><span class="sxs-lookup"><span data-stu-id="75a38-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="75a38-116">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="75a38-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="75a38-117">İki ila dört ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="75a38-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="75a38-118">Bu `year` yakalanan grup.</span><span class="sxs-lookup"><span data-stu-id="75a38-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="75a38-119">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="75a38-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="75a38-120">Desen, `${day}-${month}-${year}` aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="75a38-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="75a38-121">Desen</span><span class="sxs-lookup"><span data-stu-id="75a38-121">Pattern</span></span>|<span data-ttu-id="75a38-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75a38-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="75a38-123">`day` Yakalama grubu tarafından yakalanan dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="75a38-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="75a38-124">Tire ekle.</span><span class="sxs-lookup"><span data-stu-id="75a38-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="75a38-125">`month` Yakalama grubu tarafından yakalanan dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="75a38-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="75a38-126">Tire ekle.</span><span class="sxs-lookup"><span data-stu-id="75a38-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="75a38-127">`year` Yakalama grubu tarafından yakalanan dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="75a38-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75a38-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75a38-128">See also</span></span>

- [<span data-ttu-id="75a38-129">.NET Düzenli İfadeler</span><span class="sxs-lookup"><span data-stu-id="75a38-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
