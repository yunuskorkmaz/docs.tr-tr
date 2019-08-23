---
title: 'Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 22614be8e53d975c4efdf7004f41906c58639c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938690"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma
Saklı yordam birden çok sonuç şekli döndürebilen zaman, dönüş türü kesin bir şekilde tek bir projeksiyon şekline eklenemez. Tüm [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] olası projeksiyon türlerini oluşturabilse de, bu işlem, döndürülme sırasını bilmez.  
  
 Bu senaryoya, ardışık olarak birden çok sonuç şekli üreten Saklı yordamlarla kontrast. Daha fazla bilgi için [nasıl yapılır: Sıralı sonuç şekilleri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)Için eşlenen saklı yordamları kullanın.  
  
 <xref:System.Data.Linq.Mapping.ResultTypeAttribute> Özniteliği, yordamın döndüreabileceği tür kümesini belirtmek için birden çok sonuç türü döndüren saklı yordamlara uygulanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kod örneğinde, sonuç şekli girişe bağlıdır (`shape =1` veya `shape = 2`). İlk olarak hangi projeksiyonın döndürüleceğini bilemezsiniz.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Örnek  
 Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.  
  
> [!NOTE]
> Saklı yordamın bilgisine göre <xref:System.Data.Linq.IMultipleResults.GetResult%2A> doğru türde bir Numaralandırıcı elde etmek için bu kalıbı kullanmanız gerekir.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
