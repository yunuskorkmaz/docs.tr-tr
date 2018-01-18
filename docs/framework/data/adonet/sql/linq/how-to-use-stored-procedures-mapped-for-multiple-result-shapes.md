---
title: "Nasıl yapılır: birden çok sonuç şekiller için eşlenen saklı yordamları kullanma"
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
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fde4dd9044ff2bc6d781d7ceafec2bde3df7e14d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="2f31c-102">Nasıl yapılır: birden çok sonuç şekiller için eşlenen saklı yordamları kullanma</span><span class="sxs-lookup"><span data-stu-id="2f31c-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="2f31c-103">Saklı yordam birden çok sonuç şekil döndüğünüzde dönüş türü tek projeksiyon şekle kesin türü belirtilmiş olamaz.</span><span class="sxs-lookup"><span data-stu-id="2f31c-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="2f31c-104">Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tüm olası projeksiyon türlerinizi oluşturabilirsiniz, içinde bunlar döndürüleceği sipariş bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f31c-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="2f31c-105">Bu senaryo birden çok sonuç şekil sırayla üretmek saklı yordamlar ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="2f31c-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="2f31c-106">Daha fazla bilgi için bkz: [nasıl yapılır: kullanım depolanan yordamları eşlenen sıralı sonuç şekilleri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="2f31c-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="2f31c-107"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> Özniteliği yordamı dönebilirsiniz türleri kümesini belirtmek için birden çok sonuç türleri döndüren saklı yordamları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2f31c-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f31c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f31c-108">Example</span></span>  
 <span data-ttu-id="2f31c-109">Aşağıdaki SQL kod örneğinde, giriş, sonuç şekli bağlıdır (`shape =1` veya `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="2f31c-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="2f31c-110">Hangi projeksiyon ilk döndürülecek bilmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f31c-110">You do not know which projection will be returned first.</span></span>  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="2f31c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f31c-111">Example</span></span>  
 <span data-ttu-id="2f31c-112">Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2f31c-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f31c-113">Kullanmalısınız <xref:System.Data.Linq.IMultipleResults.GetResult%2A> , saklı yordam bilgisini temel alarak doğru türde bir numaralandırıcı almak için desen.</span><span class="sxs-lookup"><span data-stu-id="2f31c-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2f31c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f31c-114">See Also</span></span>  
 [<span data-ttu-id="2f31c-115">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2f31c-115">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
