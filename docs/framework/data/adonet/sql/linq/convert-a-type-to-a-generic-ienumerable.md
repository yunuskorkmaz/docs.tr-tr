---
title: "Bir tür için genel bir IEnumerable Dönüştür"
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
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa15e1336c31aec47fb2255f224146b9ac7e429d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Bir tür için genel bir IEnumerable Dönüştür
Kullanım <xref:System.Linq.Enumerable.AsEnumerable%2A> genel yazılan bağımsız değişkenini döndürmesine izin `IEnumerable`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (genel varsayılan kullanarak `Query`) SQL sorgu dönüştürmek ve sunucuda yürütmek isteriz. Ancak `where` yan tümcesinde başvuruda bulunan bir kullanıcı tarafından tanımlanan istemci-tarafı yöntemi (`isValidProduct`), hangi dönüştürülemiyor SQL.  
  
 İstemci-tarafı genel belirtmek için çözümdür <xref:System.Collections.Generic.IEnumerable%601> uyarlamasını `where` genel değiştirmek için <xref:System.Linq.IQueryable%601>. Harekete geçirerek bunu <xref:System.Linq.Enumerable.AsEnumerable%2A> işleci.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
