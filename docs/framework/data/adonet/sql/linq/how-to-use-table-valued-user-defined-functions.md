---
title: 'Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma'
description: Tek bir satır kümesi döndüren tablo değerli bir işlev oluşturmayı öğrenmek için bu örnekleri kullanın. Tablo değerli bir işlevi tıpkı bir tablo gibi kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 44866367393e321d7dd2db965e2fad8a2e6b63e9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286332"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a>Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma
Tablo değerli bir işlev, tek bir satır kümesi döndürür (birden çok sonuç şekli döndürebilen saklı yordamların aksine). Tablo değerli bir işlevin dönüş türü olduğundan `Table` , SQL 'de bir tabloyu kullanabileceğiniz bir tablo değerli işlevi kullanabilirsiniz. Tablo değerli işlevi tıpkı bir tablo gibi da kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL işlevi açıkça bir döndüren bildirir `TABLE` . Bu nedenle, döndürülen satır kümesi yapısı örtük olarak tanımlanmıştır.  
  
```sql
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
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, sorgu şu şekilde işlenir:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı tanımlı Işlevler](user-defined-functions.md)
