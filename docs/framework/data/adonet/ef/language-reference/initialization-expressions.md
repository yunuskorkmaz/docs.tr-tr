---
title: Başlatma İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 6f6f27eaecd760e565eeb98a286252981d6df0bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129148"
---
# <a name="initialization-expressions"></a><span data-ttu-id="7c815-102">Başlatma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7c815-102">Initialization Expressions</span></span>
<span data-ttu-id="7c815-103">Bir ifade başlatma yeni bir nesne başlatır.</span><span class="sxs-lookup"><span data-stu-id="7c815-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="7c815-104">En yeni dahil olmak üzere çoğu başlatma ifadeleri desteklenir C# 3.0 ve Visual Basic 9.0 başlatma ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="7c815-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="7c815-105">Aşağıdaki türleri başlatılır ve tarafından LINQ to Entities sorgusunda döndürülen:</span><span class="sxs-lookup"><span data-stu-id="7c815-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="7c815-106">Sıfır veya daha fazla yazılan varlığın nesnelerin veya projeksiyon kavramsal modelde tanımlı karmaşık türler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7c815-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="7c815-107">CLR türleri tarafından desteklenen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c815-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="7c815-108">Satır içi koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="7c815-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="7c815-109">Anonim türler.</span><span class="sxs-lookup"><span data-stu-id="7c815-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="7c815-110">Anonim tür başlatma, sorgu ifadesi söz dizimi aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7c815-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="7c815-111">Metot tabanlı sorgu söz dizimi aşağıdaki örnekte, anonim tür başlatma gösterir:</span><span class="sxs-lookup"><span data-stu-id="7c815-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="7c815-112">Kullanıcı tanımlı sınıf başlatma da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7c815-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="7c815-113">C# 3.0 ve Visual Basic 9.0 başlatma deseni desteklenir ve özellik alıcı ve ayarlayıcı simetrik olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="7c815-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="7c815-114">Sorgu ifadesi söz dizimi aşağıdaki örnekte, sorguda başlatılmakta özel bir sınıfı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="7c815-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="7c815-115">Metot tabanlı sorgu söz dizimi aşağıdaki örnekte, sorguda başlatılmakta özel bir sınıfı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="7c815-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7c815-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c815-116">See also</span></span>

- [<span data-ttu-id="7c815-117">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7c815-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
