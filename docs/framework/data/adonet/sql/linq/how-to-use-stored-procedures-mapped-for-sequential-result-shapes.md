---
title: 'Nasıl yapılır: sıralı sonuç şekiller için eşlenen saklı yordamları kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: ade123f10e1c9ffd6d042b45599cc6e352614e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351946"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="c15f9-102">Nasıl yapılır: sıralı sonuç şekiller için eşlenen saklı yordamları kullanma</span><span class="sxs-lookup"><span data-stu-id="c15f9-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="c15f9-103">Bu tür bir saklı yordam birden fazla sonuç şekil oluşturabilir, ancak hangi sırada sonuçların döndürülmesini bildirin.</span><span class="sxs-lookup"><span data-stu-id="c15f9-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="c15f9-104">Bu senaryo burada döndürür dizisini bilmiyorsanız senaryo ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="c15f9-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="c15f9-105">Daha fazla bilgi için bkz: [nasıl yapılır: kullanım saklı yordamları eşlenen birden çok sonuç şekilleri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="c15f9-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c15f9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c15f9-106">Example</span></span>  
 <span data-ttu-id="c15f9-107">Birden çok sonuç şekil sıralı olarak döndüren bir saklı yordam T-SQL şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c15f9-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="c15f9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c15f9-108">Example</span></span>  
 <span data-ttu-id="c15f9-109">Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c15f9-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="c15f9-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c15f9-110">See Also</span></span>  
 [<span data-ttu-id="c15f9-111">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c15f9-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
