---
title: "Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma"
ms.date: 06/30/2020
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
ms.openlocfilehash: c1d45dbcb2916af86d645d7813594f2b278bb7c2
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803878"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="9c6c0-102">Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma</span><span class="sxs-lookup"><span data-stu-id="9c6c0-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="9c6c0-103">Aşağıdaki örnek bir URL 'den protokol ve bağlantı noktası numarası ayıklar.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-103">The following example extracts a protocol and port number from a URL.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="9c6c0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c6c0-104">Example</span></span>  
 <span data-ttu-id="9c6c0-105">Örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> iletişim kuralını ve ardından bağlantı noktası numarasını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="9c6c0-106">Normal ifade deseninin `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` Aşağıdaki tabloda gösterildiği gibi yorumlanması gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="9c6c0-107">Desen</span><span class="sxs-lookup"><span data-stu-id="9c6c0-107">Pattern</span></span>|<span data-ttu-id="9c6c0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c6c0-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="9c6c0-109">Dizenin başlangıcında eşleşmeyi başlatın.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="9c6c0-110">Bir veya daha fazla sözcük karakteri eşleştir.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-110">Match one or more word characters.</span></span> <span data-ttu-id="9c6c0-111">Bu grubu adlandırın `proto` .</span><span class="sxs-lookup"><span data-stu-id="9c6c0-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="9c6c0-112">İki nokta üst üste ve ardından iki eğik çizgi ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="9c6c0-113">Eğik çizgi işareti dışında herhangi bir karakterin bir veya daha fazla tekrarı (mümkün olan en az sayıda) eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="9c6c0-114">İki nokta üst üste ve ardından bir veya daha fazla rakam karakteri ile eşleşen sıfır veya bir oluşumu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="9c6c0-115">Bu grubu adlandırın `port` .</span><span class="sxs-lookup"><span data-stu-id="9c6c0-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="9c6c0-116">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="9c6c0-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Yöntemi, `${proto}${port}` normal ifade modelinde yakalanan iki adlandırılmış grubun değerini birleştiren değiştirme sırasını genişletir.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="9c6c0-118">Özelliği tarafından döndürülen koleksiyon nesnesinden alınan dizeleri açıkça birleştirerek kullanışlı bir alternatiftir <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9c6c0-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="9c6c0-119">Örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi iki değiştirme ile birlikte kullanır `${proto}` ve `${port}` yakalanan grupları çıkış dizesine dahil eder.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="9c6c0-120"><xref:System.Text.RegularExpressions.GroupCollection>Aşağıdaki kodun gösterdiği gibi, eşleşme nesnesinden yakalanan grupları elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9c6c0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c6c0-121">See also</span></span>

- [<span data-ttu-id="9c6c0-122">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9c6c0-122">.NET Regular Expressions</span></span>](regular-expressions.md)
