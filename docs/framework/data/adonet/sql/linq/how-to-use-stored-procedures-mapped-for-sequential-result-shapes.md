---
title: "Nasıl yapılır: sıralı sonuç şekiller için eşlenen saklı yordamları kullanma"
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
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 227fe2c777d23172caba5f290d9626552af4747a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="d0491-102">Nasıl yapılır: sıralı sonuç şekiller için eşlenen saklı yordamları kullanma</span><span class="sxs-lookup"><span data-stu-id="d0491-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="d0491-103">Bu tür bir saklı yordam birden fazla sonuç şekil oluşturabilir, ancak hangi sırada sonuçların döndürülmesini bildirin.</span><span class="sxs-lookup"><span data-stu-id="d0491-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="d0491-104">Bu senaryo burada döndürür dizisini bilmiyorsanız senaryo ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="d0491-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="d0491-105">Daha fazla bilgi için bkz: [nasıl yapılır: kullanım saklı yordamları eşlenen birden çok sonuç şekilleri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="d0491-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0491-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0491-106">Example</span></span>  
 <span data-ttu-id="d0491-107">Birden çok sonuç şekil sıralı olarak döndüren bir saklı yordam T-SQL şöyledir:</span><span class="sxs-lookup"><span data-stu-id="d0491-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="d0491-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0491-108">Example</span></span>  
 <span data-ttu-id="d0491-109">Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d0491-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d0491-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0491-110">See Also</span></span>  
 [<span data-ttu-id="d0491-111">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d0491-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
