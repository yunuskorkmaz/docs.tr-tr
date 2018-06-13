---
title: Başlatma ifadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 352bda826c3b872d06252e168abfb1129f178bf8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762214"
---
# <a name="initialization-expressions"></a><span data-ttu-id="3a2d9-102">Başlatma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="3a2d9-102">Initialization Expressions</span></span>
<span data-ttu-id="3a2d9-103">Başlatma ifade yeni bir nesne başlatır.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="3a2d9-104">Çoğu yeni C# 3.0 ve Visual Basic 9.0 başlatma ifadeleri de dahil olmak üzere çoğu başlatma ifadeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="3a2d9-105">Aşağıdaki türler başlatıldı ve varlıkları sorgu için bir LINQ tarafından döndürülen:</span><span class="sxs-lookup"><span data-stu-id="3a2d9-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="3a2d9-106">Sıfır veya daha fazla belirtilmiş varlık nesnesi ya da projeksiyon, kavramsal modelde tanımlanan karmaşık türler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="3a2d9-107">CLR türleri tarafından desteklenen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a2d9-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="3a2d9-108">Satır içi koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="3a2d9-109">Anonim türler.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="3a2d9-110">Anonim tür başlatma sorgu ifade sözdizimi aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a2d9-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="3a2d9-111">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte anonim tür başlatma gösterir:</span><span class="sxs-lookup"><span data-stu-id="3a2d9-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="3a2d9-112">Kullanıcı tanımlı sınıfı başlatma de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="3a2d9-113">C# 3.0 ve Visual Basic 9.0 başlatma düzeni desteklenir ve özellik Set'yordamı simetrik olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="3a2d9-114">Sorgu ifade sözdizimi aşağıdaki örnekte sorguda başlatılmakta özel bir sınıf gösterir:</span><span class="sxs-lookup"><span data-stu-id="3a2d9-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="3a2d9-115">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte sorguda başlatılmakta özel bir sınıf gösterir:</span><span class="sxs-lookup"><span data-stu-id="3a2d9-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="3a2d9-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a2d9-116">See Also</span></span>  
 [<span data-ttu-id="3a2d9-117">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3a2d9-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
