---
title: 'Nasıl yapılır: birden çok sonuç şekli için eşlenmiş saklı yordamları kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 065e866ec5937c4af31c0b1563a7582cb4112eba
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003276"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="591cb-102">Nasıl yapılır: birden çok sonuç şekli için eşlenmiş saklı yordamları kullanma</span><span class="sxs-lookup"><span data-stu-id="591cb-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="591cb-103">Saklı yordam birden çok sonuç şekli döndürebilen zaman, dönüş türü kesin bir şekilde tek bir projeksiyon şekline eklenemez.</span><span class="sxs-lookup"><span data-stu-id="591cb-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="591cb-104">@No__t-0 tüm olası projeksiyon türlerini oluşturabilse de, bu işlem, döndürülecek sırayı bilmez.</span><span class="sxs-lookup"><span data-stu-id="591cb-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="591cb-105">Bu senaryoya, ardışık olarak birden çok sonuç şekli üreten Saklı yordamlarla kontrast.</span><span class="sxs-lookup"><span data-stu-id="591cb-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="591cb-106">Daha fazla bilgi için bkz. [nasıl yapılır: sıralı sonuç şekilleri Için eşlenmiş saklı yordamları kullanma](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="591cb-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="591cb-107">@No__t-0 özniteliği, yordamın döndüreabileceği tür kümesini belirtmek için birden çok sonuç türü döndüren saklı yordamlara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="591cb-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="591cb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="591cb-108">Example</span></span>  
 <span data-ttu-id="591cb-109">Aşağıdaki SQL kod örneğinde, sonuç şekli girişe bağlıdır (`shape =1` veya `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="591cb-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="591cb-110">İlk olarak hangi projeksiyonın döndürüleceğini bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="591cb-110">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="591cb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="591cb-111">Example</span></span>  
 <span data-ttu-id="591cb-112">Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="591cb-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="591cb-113">Saklı yordamın bilgisine göre doğru türde bir Numaralandırıcı elde etmek için <xref:System.Data.Linq.IMultipleResults.GetResult%2A> deseninin kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="591cb-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="591cb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="591cb-114">See also</span></span>

- [<span data-ttu-id="591cb-115">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="591cb-115">Stored Procedures</span></span>](stored-procedures.md)
