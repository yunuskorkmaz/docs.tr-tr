---
title: 'Nasıl yapılır: Sıralı sonuç şekilleri için eşlenmiş saklı yordamlar kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 296870029d2329640466b3a540e9057738173aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495662"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="919ec-102">Nasıl yapılır: Sıralı sonuç şekilleri için eşlenmiş saklı yordamlar kullanma</span><span class="sxs-lookup"><span data-stu-id="919ec-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="919ec-103">Bu tür bir saklı yordam birden çok sonuç şekli oluşturabilirsiniz, ancak bildiğiniz hangi sırayla sonuçlar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="919ec-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="919ec-104">Bu senaryo, burada bir dizi döndürür bilmediğiniz senaryo ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="919ec-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="919ec-105">Daha fazla bilgi için [nasıl yapılır: Birden çok sonuç şekli için eşlenmiş saklı yordamlar kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="919ec-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="919ec-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="919ec-106">Example</span></span>  
 <span data-ttu-id="919ec-107">T-SQL birden çok sonuç şekli sıralı olarak döndüren bir saklı yordam şöyledir:</span><span class="sxs-lookup"><span data-stu-id="919ec-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="919ec-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="919ec-108">Example</span></span>  
 <span data-ttu-id="919ec-109">Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="919ec-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="919ec-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="919ec-110">See also</span></span>
- [<span data-ttu-id="919ec-111">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="919ec-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
