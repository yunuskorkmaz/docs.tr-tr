---
title: 'Nasıl yapılır: kullanıcı tanımlı tablo değerli işlevler kullanın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: e0199bb0a783f54931885053681c48d288012404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362905"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a>Nasıl yapılır: kullanıcı tanımlı tablo değerli işlevler kullanın
Tablo değerli bir işlev (aksine, saklı yordamlar, birden çok sonuç şekil dönebilirsiniz) tek bir satır kümesi döndürür. Tablo değerli bir işlev dönüş türü olduğundan `Table`, tablo değerli bir işlev tablo kullanabileceğiniz SQL her yerde kullanabilirsiniz. Bir tablo gibi tablo değerli işlevi de davranabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL işlev açıkça döndürdüğü bildiren bir `TABLE`. Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanır.  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işlev şu şekilde eşlenir:  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kod işlevi döndürür tablo birleştirme ve aksi takdirde, başka bir tablo gibi davran gösterir:  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sorgu şu şekilde oluşturulması:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
