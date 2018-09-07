---
title: "Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma"
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a08e97b02e2f60422132e97e2f3f7d4d2d5b8ec4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061669"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="41a2f-102">Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma</span><span class="sxs-lookup"><span data-stu-id="41a2f-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="41a2f-103">Aşağıdaki örnek, bir URL'den protokol ve bağlantı noktası numarası ayıklar.</span><span class="sxs-lookup"><span data-stu-id="41a2f-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41a2f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="41a2f-104">Example</span></span>  
 <span data-ttu-id="41a2f-105">Örnekte <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> bağlantı noktası numarası ile üste arkasından Protokolü döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41a2f-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="41a2f-106">Normal ifade deseni `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` aşağıdaki tabloda gösterildiği gibi yorumlanabilir.</span><span class="sxs-lookup"><span data-stu-id="41a2f-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="41a2f-107">Desen</span><span class="sxs-lookup"><span data-stu-id="41a2f-107">Pattern</span></span>|<span data-ttu-id="41a2f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41a2f-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="41a2f-109">Dizesinin başında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="41a2f-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="41a2f-110">Bir veya daha fazla sözcük karakteri eşleştir.</span><span class="sxs-lookup"><span data-stu-id="41a2f-110">Match one or more word characters.</span></span> <span data-ttu-id="41a2f-111">Bu gruba adını `proto`.</span><span class="sxs-lookup"><span data-stu-id="41a2f-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="41a2f-112">Üste iki eğik çizgi işaretleriyle eşleş.</span><span class="sxs-lookup"><span data-stu-id="41a2f-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="41a2f-113">Bir veya daha çok tekrarı (ama olabildiğince az sayıda) eğik çizgi işareti dışındaki herhangi bir karakterle eşleş.</span><span class="sxs-lookup"><span data-stu-id="41a2f-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="41a2f-114">Bir veya daha fazla basamak karakterleri üste sıfır veya bir oluşumunu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="41a2f-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="41a2f-115">Bu gruba adını `port`.</span><span class="sxs-lookup"><span data-stu-id="41a2f-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="41a2f-116">Bir eğik çizgi işareti eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="41a2f-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="41a2f-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntemi genişletir `${proto}${port}` değeri normal ifade deseninde yakalanan iki adlandırılmış gruplar, sıralar değiştirme dizisi.</span><span class="sxs-lookup"><span data-stu-id="41a2f-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="41a2f-118">Açıkça tarafından döndürülen koleksiyon nesnesinden alınan dizeleri birleştirirken için kullanışlı bir alternatiftir <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="41a2f-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="41a2f-119">Örnekte <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> iki değişimler yöntemiyle `${proto}` ve `${port}`, çıktı dizesinde yakalanan gruplar eklemek için.</span><span class="sxs-lookup"><span data-stu-id="41a2f-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="41a2f-120">Eşleşmeden 's yakalanan gruplar alabilirsiniz <xref:System.Text.RegularExpressions.GroupCollection> bunun yerine, aşağıdaki kodun gösterdiği nesne.</span><span class="sxs-lookup"><span data-stu-id="41a2f-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="41a2f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41a2f-121">See also</span></span>

- [<span data-ttu-id="41a2f-122">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="41a2f-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
