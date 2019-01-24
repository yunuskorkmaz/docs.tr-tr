---
title: 'Nasıl yapılır: Parametre alan saklı yordamlar kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: b81cb3b7428ba2ed4e958e18e9368f6f774e8ee3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604256"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Nasıl yapılır: Parametre alan saklı yordamlar kullanma
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] başvuru parametreleri için çıktı parametreleri eşlenir ve buna değer türleri için parametre olarak boş değer atanabilir bildirir.  
  
 Giriş parametresi bir satır kümesi döndüren bir sorgu kullanma örneği için bkz: [nasıl yapılır: Satır kümeleri iade](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir giriş parametresi (Müşteri Kimliği) alır ve out parametresi (o müşteri için toplam satış) döndürür.  
  
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
 Bu saklı yordamı şu şekilde çağırırsınız:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Boş Değer Atanabilir Tipleri Kullanma](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Boş Değer Atanabilen Değer Türleri](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
