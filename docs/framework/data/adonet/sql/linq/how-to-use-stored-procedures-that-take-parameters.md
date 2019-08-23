---
title: 'Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 17ae74a430df4d4a4670c2390ce7b2ee25b67c7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938707"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çıkış parametrelerini başvuru parametrelerine eşler ve değer türleri için parametreyi null yapılabilir olarak bildirir.  
  
 Bir satır kümesi döndüren sorguda giriş parametresinin nasıl kullanılacağına ilişkin bir örnek için bkz [. nasıl yapılır: Satır kümelerini](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)döndürün.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tek bir giriş parametresi (müşteri KIMLIĞI) alır ve bir out parametresi (bu müşterinin toplam satışları) döndürür.  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a>Örnek  
 Bu saklı yordamı aşağıdaki şekilde çağırabilirsiniz:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Boş Değer Atanabilir Tipleri Kullanma](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Boş Değer Atanabilen Değer Türleri](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
