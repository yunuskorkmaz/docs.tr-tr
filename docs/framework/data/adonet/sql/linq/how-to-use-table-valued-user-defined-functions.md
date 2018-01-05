---
title: "Nasıl yapılır: kullanıcı tanımlı tablo değerli işlevler kullanın"
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
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 63e2ee9dffb041ede094afd43428660af4b9f450
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="21b61-102">Nasıl yapılır: kullanıcı tanımlı tablo değerli işlevler kullanın</span><span class="sxs-lookup"><span data-stu-id="21b61-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="21b61-103">Tablo değerli bir işlev (aksine, saklı yordamlar, birden çok sonuç şekil dönebilirsiniz) tek bir satır kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="21b61-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="21b61-104">Tablo değerli bir işlev dönüş türü olduğundan `Table`, tablo değerli bir işlev tablo kullanabileceğiniz SQL her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21b61-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="21b61-105">Bir tablo gibi tablo değerli işlevi de davranabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21b61-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21b61-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="21b61-106">Example</span></span>  
 <span data-ttu-id="21b61-107">Aşağıdaki SQL işlev açıkça döndürdüğü bildiren bir `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="21b61-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="21b61-108">Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="21b61-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="21b61-109">işlev şu şekilde eşlenir:</span><span class="sxs-lookup"><span data-stu-id="21b61-109"> maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="21b61-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="21b61-110">Example</span></span>  
 <span data-ttu-id="21b61-111">Aşağıdaki SQL kod işlevi döndürür tablo birleştirme ve aksi takdirde, başka bir tablo gibi davran gösterir:</span><span class="sxs-lookup"><span data-stu-id="21b61-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="21b61-112">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sorgu şu şekilde oluşturulması:</span><span class="sxs-lookup"><span data-stu-id="21b61-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="21b61-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21b61-113">See Also</span></span>  
 [<span data-ttu-id="21b61-114">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="21b61-114">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
