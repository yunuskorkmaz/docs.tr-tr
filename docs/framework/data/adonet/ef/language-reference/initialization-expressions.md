---
title: Başlatma İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 109be8ef2bf41326fcab5896ecdc359859683345
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250679"
---
# <a name="initialization-expressions"></a><span data-ttu-id="9f176-102">Başlatma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9f176-102">Initialization Expressions</span></span>
<span data-ttu-id="9f176-103">Bir başlatma ifadesi yeni bir nesnesi başlatır.</span><span class="sxs-lookup"><span data-stu-id="9f176-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="9f176-104">En yeni C# 3,0 ve Visual Basic 9,0 başlatma ifadeleri dahil olmak üzere çoğu başlatma ifadesi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9f176-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="9f176-105">Aşağıdaki türler LINQ to Entities bir sorgu tarafından başlatılabilir ve döndürülebilir:</span><span class="sxs-lookup"><span data-stu-id="9f176-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="9f176-106">Sıfır veya daha fazla yazılmış varlık nesnesi koleksiyonu veya kavramsal modelde tanımlanan karmaşık türlerin projeksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9f176-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="9f176-107">Tarafından desteklenen CLR türleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f176-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="9f176-108">Satır içi Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="9f176-108">Inline collections.</span></span>  
  
- <span data-ttu-id="9f176-109">Anonim türler.</span><span class="sxs-lookup"><span data-stu-id="9f176-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="9f176-110">Anonim tür başlatma sorgu ifadesi sözdiziminde aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f176-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="9f176-111">Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek anonim tür başlatmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9f176-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="9f176-112">Kullanıcı tanımlı sınıf başlatması de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9f176-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="9f176-113">C# 3,0 ve Visual Basic 9,0 başlatma kalıbı desteklenir ve özellik alıcısı ve ayarlayıcının simetrik olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9f176-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="9f176-114">Sorgu ifadesi sözdiziminde aşağıdaki örnek, sorguda başlatılmakta olan özel bir sınıfı gösterir:</span><span class="sxs-lookup"><span data-stu-id="9f176-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="9f176-115">Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, sorguda başlatılmakta olan özel bir sınıfı gösterir:</span><span class="sxs-lookup"><span data-stu-id="9f176-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="9f176-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f176-116">See also</span></span>

- [<span data-ttu-id="9f176-117">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9f176-117">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
