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
ms.openlocfilehash: 58a1803618845e3914d57d425a1b3d1e5e857aac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]işlev şu şekilde eşlenir:  
  
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
 [Kullanıcı tanımlı işlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
