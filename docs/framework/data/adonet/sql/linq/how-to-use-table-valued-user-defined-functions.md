---
title: 'Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 31797ae7d0fe23227cc4af733fbceac5d474f779
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781450"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a>Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma
Tablo değerli bir işlev, tek bir satır kümesi döndürür (birden çok sonuç şekli döndürebilen saklı yordamların aksine). Tablo değerli bir işlevin `Table`dönüş türü olduğundan, SQL 'de bir tabloyu kullanabileceğiniz bir tablo değerli işlevi kullanabilirsiniz. Tablo değerli işlevi tıpkı bir tablo gibi da kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL işlevi açıkça bir `TABLE`döndüren bildirir. Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanmıştır.  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]işlevi şu şekilde eşler:  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kodu, işlevin döndürdüğü tabloya katılabileceğinizi gösterir ve başka herhangi bir tablo gibi kabul eder:  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 ' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, sorgu şu şekilde işlenir:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı Tanımlı İşlevler](user-defined-functions.md)
