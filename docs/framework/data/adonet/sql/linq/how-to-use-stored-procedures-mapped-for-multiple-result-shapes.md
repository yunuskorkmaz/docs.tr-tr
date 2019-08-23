---
title: 'Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 22614be8e53d975c4efdf7004f41906c58639c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938690"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="ade3d-102">Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="ade3d-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="ade3d-103">Saklı yordam birden çok sonuç şekli döndürebilen zaman, dönüş türü kesin bir şekilde tek bir projeksiyon şekline eklenemez.</span><span class="sxs-lookup"><span data-stu-id="ade3d-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="ade3d-104">Tüm [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] olası projeksiyon türlerini oluşturabilse de, bu işlem, döndürülme sırasını bilmez.</span><span class="sxs-lookup"><span data-stu-id="ade3d-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="ade3d-105">Bu senaryoya, ardışık olarak birden çok sonuç şekli üreten Saklı yordamlarla kontrast.</span><span class="sxs-lookup"><span data-stu-id="ade3d-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="ade3d-106">Daha fazla bilgi için [nasıl yapılır: Sıralı sonuç şekilleri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)Için eşlenen saklı yordamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="ade3d-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="ade3d-107"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> Özniteliği, yordamın döndüreabileceği tür kümesini belirtmek için birden çok sonuç türü döndüren saklı yordamlara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ade3d-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ade3d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ade3d-108">Example</span></span>  
 <span data-ttu-id="ade3d-109">Aşağıdaki SQL kod örneğinde, sonuç şekli girişe bağlıdır (`shape =1` veya `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="ade3d-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="ade3d-110">İlk olarak hangi projeksiyonın döndürüleceğini bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ade3d-110">You do not know which projection will be returned first.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ade3d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ade3d-111">Example</span></span>  
 <span data-ttu-id="ade3d-112">Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ade3d-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ade3d-113">Saklı yordamın bilgisine göre <xref:System.Data.Linq.IMultipleResults.GetResult%2A> doğru türde bir Numaralandırıcı elde etmek için bu kalıbı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ade3d-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ade3d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ade3d-114">See also</span></span>

- [<span data-ttu-id="ade3d-115">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ade3d-115">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
