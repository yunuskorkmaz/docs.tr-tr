---
title: 'Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: d32faf026789923ca4343271c9fd1b6bbdb068df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793100"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Nasıl yapılır: Birden Çok Sonuç Şekli İçin Eşlenmiş Saklı Yordamlar Kullanma
Saklı yordam birden çok sonuç şekli döndürebilen zaman, dönüş türü kesin bir şekilde tek bir projeksiyon şekline eklenemez. Tüm [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] olası projeksiyon türlerini oluşturabilse de, bu işlem, döndürülme sırasını bilmez.  
  
 Bu senaryoya, ardışık olarak birden çok sonuç şekli üreten Saklı yordamlarla kontrast. Daha fazla bilgi için [nasıl yapılır: Sıralı sonuç şekilleri](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)Için eşlenen saklı yordamları kullanın.  
  
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

- [Saklı Yordamlar](stored-procedures.md)
