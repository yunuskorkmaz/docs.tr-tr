---
title: 'Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: eedc2e9b997e91ed9fe0038f260aa475d23a0627
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033598"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="9dc30-102">Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="9dc30-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="9dc30-103">Tek bir satır kümesi (aksine, saklı yordamlar, birden çok sonuç şekli dönebilirsiniz) tablo değerli bir işlev döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dc30-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="9dc30-104">Tablo değerli bir işlev dönüş türü olduğundan `Table`, bir tablo değerli işlev bir tablo kullanabileceğiniz SQL her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc30-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="9dc30-105">Bir tablo gibi tablo değerli işlev ayrıca davranabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dc30-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dc30-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dc30-106">Example</span></span>  
 <span data-ttu-id="9dc30-107">Aşağıdaki SQL işlevi açıkça döndürür bildiren bir `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="9dc30-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="9dc30-108">Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9dc30-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9dc30-109">işlev şu şekilde eşlenir:</span><span class="sxs-lookup"><span data-stu-id="9dc30-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9dc30-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dc30-110">Example</span></span>  
 <span data-ttu-id="9dc30-111">Aşağıdaki SQL kod işlevinin döndürdüğü tablo katılın ve aksi takdirde, diğer tablolar gibi davran gösterir:</span><span class="sxs-lookup"><span data-stu-id="9dc30-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="9dc30-112">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sorguyu şu şekilde işlenir:</span><span class="sxs-lookup"><span data-stu-id="9dc30-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9dc30-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dc30-113">See also</span></span>

- [<span data-ttu-id="9dc30-114">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="9dc30-114">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
