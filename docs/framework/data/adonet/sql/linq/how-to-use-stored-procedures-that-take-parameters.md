---
title: 'Nasıl yapılır: parametre alma saklı yordamlarını kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: faf4ea9c52b91c3fc0f2f775e7bd5dfe039c53a8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738118"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Nasıl yapılır: parametre alma saklı yordamlarını kullanma
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çıkış parametrelerini başvuru parametrelerine eşler ve değer türleri için parametreyi null yapılabilir olarak bildirir.  
  
 Bir satır kümesi döndüren sorguda giriş parametresinin nasıl kullanılacağına ilişkin bir örnek için bkz. [nasıl yapılır: satır kümelerini döndürme](how-to-return-rowsets.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tek bir giriş parametresi (müşteri KIMLIĞI) alır ve bir out parametresi (bu müşterinin toplam satışları) döndürür.  
  
```sql
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

- [Saklı Yordamlar](stored-procedures.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Nullable değer türleri (C#)](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [Nullable değer türleri (Visual Basic)](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
