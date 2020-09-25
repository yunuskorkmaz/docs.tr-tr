---
title: Başlatma İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 93f590e1c177adf541baca85a48fee5f9eb8d1d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203637"
---
# <a name="initialization-expressions"></a>Başlatma İfadeleri

Bir başlatma ifadesi yeni bir nesnesi başlatır. En yeni C# 3,0 ve Visual Basic 9,0 başlatma ifadeleri dahil olmak üzere çoğu başlatma ifadesi desteklenir. Aşağıdaki türler LINQ to Entities bir sorgu tarafından başlatılabilir ve döndürülebilir:  
  
- Sıfır veya daha fazla yazılmış varlık nesnesi koleksiyonu veya kavramsal modelde tanımlanan karmaşık türlerin projeksiyonu.  
  
- Entity Framework tarafından desteklenen CLR türleri.
  
- Satır içi Koleksiyonlar.  
  
- Anonim türler.  
  
 Anonim tür başlatma sorgu ifadesi sözdiziminde aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek anonim tür başlatmasını gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 Kullanıcı tanımlı sınıf başlatması de desteklenir. C# 3,0 ve Visual Basic 9,0 başlatma kalıbı desteklenir ve özellik alıcısı ve ayarlayıcının simetrik olduğunu varsayar. Sorgu ifadesi sözdiziminde aşağıdaki örnek, sorguda başlatılmakta olan özel bir sınıfı gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, sorguda başlatılmakta olan özel bir sınıfı gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
