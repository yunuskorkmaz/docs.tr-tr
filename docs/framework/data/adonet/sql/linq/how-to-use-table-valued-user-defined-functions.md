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
# <a name="how-to-use-table-valued-user-defined-functions"></a>Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma
Tek bir satır kümesi (aksine, saklı yordamlar, birden çok sonuç şekli dönebilirsiniz) tablo değerli bir işlev döndürür. Tablo değerli bir işlev dönüş türü olduğundan `Table`, bir tablo değerli işlev bir tablo kullanabileceğiniz SQL her yerde kullanabilirsiniz. Bir tablo gibi tablo değerli işlev ayrıca davranabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL işlevi açıkça döndürür bildiren bir `TABLE`. Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanır.  
  
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
 Aşağıdaki SQL kod işlevinin döndürdüğü tablo katılın ve aksi takdirde, diğer tablolar gibi davran gösterir:  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sorguyu şu şekilde işlenir:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
