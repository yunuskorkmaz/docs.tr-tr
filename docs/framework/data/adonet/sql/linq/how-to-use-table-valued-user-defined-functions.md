---
title: 'Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma'
description: Tek bir satır kümesi döndüren tablo değerli bir işlev oluşturmayı öğrenmek için bu örnekleri kullanın. Tablo değerli bir işlevi tıpkı bir tablo gibi kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 68a2b54c8fd541595d36bf9c864257b1be1f7856
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203585"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="0e1a7-104">Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e1a7-104">How to: Use Table-Valued User-Defined Functions</span></span>

<span data-ttu-id="0e1a7-105">Tablo değerli bir işlev, tek bir satır kümesi döndürür (birden çok sonuç şekli döndürebilen saklı yordamların aksine).</span><span class="sxs-lookup"><span data-stu-id="0e1a7-105">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="0e1a7-106">Tablo değerli bir işlevin dönüş türü olduğundan `Table` , SQL 'de bir tabloyu kullanabileceğiniz bir tablo değerli işlevi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e1a7-106">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="0e1a7-107">Tablo değerli işlevi tıpkı bir tablo gibi da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e1a7-107">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e1a7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e1a7-108">Example</span></span>  

 <span data-ttu-id="0e1a7-109">Aşağıdaki SQL işlevi açıkça bir döndüren bildirir `TABLE` .</span><span class="sxs-lookup"><span data-stu-id="0e1a7-109">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="0e1a7-110">Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e1a7-110">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0e1a7-111">işlevi şu şekilde eşler:</span><span class="sxs-lookup"><span data-stu-id="0e1a7-111">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="0e1a7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e1a7-112">Example</span></span>  

 <span data-ttu-id="0e1a7-113">Aşağıdaki SQL kodu, işlevin döndürdüğü tabloya katılabileceğinizi gösterir ve başka herhangi bir tablo gibi kabul eder:</span><span class="sxs-lookup"><span data-stu-id="0e1a7-113">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="0e1a7-114">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, sorgu şu şekilde işlenir:</span><span class="sxs-lookup"><span data-stu-id="0e1a7-114">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0e1a7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e1a7-115">See also</span></span>

- [<span data-ttu-id="0e1a7-116">Kullanıcı tanımlı Işlevler</span><span class="sxs-lookup"><span data-stu-id="0e1a7-116">User-Defined Functions</span></span>](user-defined-functions.md)
