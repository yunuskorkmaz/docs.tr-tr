---
title: "Başlatma ifadeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3fc3b4b2fdbec6c527f6240460a263f40e683177
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="initialization-expressions"></a><span data-ttu-id="4491f-102">Başlatma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="4491f-102">Initialization Expressions</span></span>
<span data-ttu-id="4491f-103">Başlatma ifade yeni bir nesne başlatır.</span><span class="sxs-lookup"><span data-stu-id="4491f-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="4491f-104">Çoğu yeni C# 3.0 ve Visual Basic 9.0 başlatma ifadeleri de dahil olmak üzere çoğu başlatma ifadeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4491f-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="4491f-105">Aşağıdaki türler başlatıldı ve varlıkları sorgu için bir LINQ tarafından döndürülen:</span><span class="sxs-lookup"><span data-stu-id="4491f-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="4491f-106">Sıfır veya daha fazla belirtilmiş varlık nesnesi ya da projeksiyon, kavramsal modelde tanımlanan karmaşık türler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4491f-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="4491f-107">CLR türleri tarafından desteklenen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4491f-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="4491f-108">Satır içi koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="4491f-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="4491f-109">Anonim türler.</span><span class="sxs-lookup"><span data-stu-id="4491f-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="4491f-110">Anonim tür başlatma sorgu ifade sözdizimi aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4491f-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="4491f-111">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte anonim tür başlatma gösterir:</span><span class="sxs-lookup"><span data-stu-id="4491f-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="4491f-112">Kullanıcı tanımlı sınıfı başlatma de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4491f-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="4491f-113">C# 3.0 ve Visual Basic 9.0 başlatma düzeni desteklenir ve özellik Set'yordamı simetrik olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="4491f-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="4491f-114">Sorgu ifade sözdizimi aşağıdaki örnekte sorguda başlatılmakta özel bir sınıf gösterir:</span><span class="sxs-lookup"><span data-stu-id="4491f-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="4491f-115">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte sorguda başlatılmakta özel bir sınıf gösterir:</span><span class="sxs-lookup"><span data-stu-id="4491f-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4491f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4491f-116">See Also</span></span>  
 [<span data-ttu-id="4491f-117">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="4491f-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
