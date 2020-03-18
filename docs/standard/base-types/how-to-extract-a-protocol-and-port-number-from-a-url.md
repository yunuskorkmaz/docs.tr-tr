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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138729"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="e30b9-102">Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma</span><span class="sxs-lookup"><span data-stu-id="e30b9-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="e30b9-103">Aşağıdaki örnek, bir URL'den bir protokol ve bağlantı noktası numarası ayıklar.</span><span class="sxs-lookup"><span data-stu-id="e30b9-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e30b9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e30b9-104">Example</span></span>  
 <span data-ttu-id="e30b9-105">Örnek, bağlantı <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> noktası numarası nın ardından bir nokta üst üste gelen protokolü döndürmek için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e30b9-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="e30b9-106">Normal ifade `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` deseni aşağıdaki tabloda gösterildiği gibi yorumlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e30b9-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="e30b9-107">Desen</span><span class="sxs-lookup"><span data-stu-id="e30b9-107">Pattern</span></span>|<span data-ttu-id="e30b9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e30b9-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="e30b9-109">Dize başında maç başlayın.</span><span class="sxs-lookup"><span data-stu-id="e30b9-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="e30b9-110">Bir veya daha fazla sözcük karakteri eşleştir.</span><span class="sxs-lookup"><span data-stu-id="e30b9-110">Match one or more word characters.</span></span> <span data-ttu-id="e30b9-111">Bu gruba `proto`isim verem.</span><span class="sxs-lookup"><span data-stu-id="e30b9-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="e30b9-112">Bir iki nokta üst üste iki eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="e30b9-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="e30b9-113">Eğik çizgi işareti dışında herhangi bir karakterin bir veya daha fazla oluşumunu (ancak mümkün olduğunca az) eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="e30b9-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="e30b9-114">Bir veya daha fazla basamak lı karakter tarafından izlenen bir iki nokta üst üste sıfır veya bir oluşum eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="e30b9-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="e30b9-115">Bu gruba `port`isim verem.</span><span class="sxs-lookup"><span data-stu-id="e30b9-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="e30b9-116">Eğik çizgi işaretini eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="e30b9-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="e30b9-117">Yöntem, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> normal `${proto}${port}` ifade deseninde yakalanan iki adlandırılmış grubun değerini biraraya getiren değiştirme sırasını genişletir.</span><span class="sxs-lookup"><span data-stu-id="e30b9-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="e30b9-118">Özellik tarafından döndürülen koleksiyon nesnesinden alınan dizeleri açıkça bağlamak <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> için kullanışlı bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="e30b9-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e30b9-119">Örnek, `${proto}` yakalanan grupları çıktı dizesine `${port}`dahil etmek için iki değişiklik le <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e30b9-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="e30b9-120">Yakalanan grupları aşağıdaki kodun gösterdiği <xref:System.Text.RegularExpressions.GroupCollection> gibi, bunun yerine eşleşmenin nesnesinden alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e30b9-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e30b9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e30b9-121">See also</span></span>

- [<span data-ttu-id="e30b9-122">.NET Düzenli İfadeler</span><span class="sxs-lookup"><span data-stu-id="e30b9-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
