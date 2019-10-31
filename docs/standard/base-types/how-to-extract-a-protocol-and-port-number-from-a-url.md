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
ms.openlocfilehash: f2704e3fb5ceb68609a475d52e11030177ad760b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138729"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="52912-102">Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma</span><span class="sxs-lookup"><span data-stu-id="52912-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="52912-103">Aşağıdaki örnek bir URL 'den protokol ve bağlantı noktası numarası ayıklar.</span><span class="sxs-lookup"><span data-stu-id="52912-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52912-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="52912-104">Example</span></span>  
 <span data-ttu-id="52912-105">Örnek, ardından bağlantı noktası numarasını izleyen bir iki nokta üst üste gelen kuralı döndürmek için <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="52912-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="52912-106">`^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` normal ifade deseninin aşağıdaki tabloda gösterildiği gibi yorumlanması gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="52912-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="52912-107">Desen</span><span class="sxs-lookup"><span data-stu-id="52912-107">Pattern</span></span>|<span data-ttu-id="52912-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52912-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="52912-109">Dizenin başlangıcında eşleşmeyi başlatın.</span><span class="sxs-lookup"><span data-stu-id="52912-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="52912-110">Bir veya daha fazla sözcük karakteri eşleştir.</span><span class="sxs-lookup"><span data-stu-id="52912-110">Match one or more word characters.</span></span> <span data-ttu-id="52912-111">Bu grubun `proto`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="52912-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="52912-112">İki nokta üst üste ve ardından iki eğik çizgi ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="52912-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="52912-113">Eğik çizgi işareti dışında herhangi bir karakterin bir veya daha fazla tekrarı (mümkün olan en az sayıda) eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="52912-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="52912-114">İki nokta üst üste ve ardından bir veya daha fazla rakam karakteri ile eşleşen sıfır veya bir oluşumu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="52912-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="52912-115">Bu grubun `port`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="52912-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="52912-116">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="52912-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="52912-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi, normal ifade modelinde yakalanan iki adlandırılmış grubun değerini birleştiren `${proto}${port}` değiştirme sırasını genişletir.</span><span class="sxs-lookup"><span data-stu-id="52912-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="52912-118"><xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği tarafından döndürülen koleksiyon nesnesinden alınan dizeleri açıkça birleştirerek kullanışlı bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="52912-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="52912-119">Örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemini, `${proto}` ve `${port}`olmak üzere iki değişim ile kullanır. Bu, yakalanan grupları çıkış dizesine dahil eder.</span><span class="sxs-lookup"><span data-stu-id="52912-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="52912-120">Aşağıdaki kodun gösterdiği gibi, eşleşme <xref:System.Text.RegularExpressions.GroupCollection> nesnesinden yakalanan grupları alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52912-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="52912-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52912-121">See also</span></span>

- [<span data-ttu-id="52912-122">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="52912-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
