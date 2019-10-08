---
title: 'Nasıl yapılır: tablo değerli Kullanıcı tanımlı Işlevleri kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: c4b5290e4f1aa69c7f55951d526ccb303a5a95ec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003177"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="0d088-102">Nasıl yapılır: tablo değerli Kullanıcı tanımlı Işlevleri kullanma</span><span class="sxs-lookup"><span data-stu-id="0d088-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="0d088-103">Tablo değerli bir işlev, tek bir satır kümesi döndürür (birden çok sonuç şekli döndürebilen saklı yordamların aksine).</span><span class="sxs-lookup"><span data-stu-id="0d088-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="0d088-104">Tablo değerli bir işlevin dönüş türü `Table` olduğundan, SQL 'de bir tabloyu kullanabileceğiniz bir tablo değerli işlevi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d088-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="0d088-105">Tablo değerli işlevi tıpkı bir tablo gibi da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d088-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d088-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d088-106">Example</span></span>  
 <span data-ttu-id="0d088-107">Aşağıdaki SQL işlevi, `TABLE` döndürdüğünü açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d088-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="0d088-108">Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0d088-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0d088-109">işlevi şu şekilde eşler:</span><span class="sxs-lookup"><span data-stu-id="0d088-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="0d088-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d088-110">Example</span></span>  
 <span data-ttu-id="0d088-111">Aşağıdaki SQL kodu, işlevin döndürdüğü tabloya katılabileceğinizi gösterir ve başka herhangi bir tablo gibi kabul eder:</span><span class="sxs-lookup"><span data-stu-id="0d088-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="0d088-112">@No__t-0 ' da, sorgu şu şekilde işlenir:</span><span class="sxs-lookup"><span data-stu-id="0d088-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0d088-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d088-113">See also</span></span>

- [<span data-ttu-id="0d088-114">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="0d088-114">User-Defined Functions</span></span>](user-defined-functions.md)
