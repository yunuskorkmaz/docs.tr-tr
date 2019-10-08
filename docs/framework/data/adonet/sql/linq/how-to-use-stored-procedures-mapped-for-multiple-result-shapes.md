---
title: 'Nasıl yapılır: birden çok sonuç şekli için eşlenmiş saklı yordamları kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 065e866ec5937c4af31c0b1563a7582cb4112eba
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003276"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Nasıl yapılır: birden çok sonuç şekli için eşlenmiş saklı yordamları kullanma
Saklı yordam birden çok sonuç şekli döndürebilen zaman, dönüş türü kesin bir şekilde tek bir projeksiyon şekline eklenemez. @No__t-0 tüm olası projeksiyon türlerini oluşturabilse de, bu işlem, döndürülecek sırayı bilmez.  
  
 Bu senaryoya, ardışık olarak birden çok sonuç şekli üreten Saklı yordamlarla kontrast. Daha fazla bilgi için bkz. [nasıl yapılır: sıralı sonuç şekilleri Için eşlenmiş saklı yordamları kullanma](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 @No__t-0 özniteliği, yordamın döndüreabileceği tür kümesini belirtmek için birden çok sonuç türü döndüren saklı yordamlara uygulanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kod örneğinde, sonuç şekli girişe bağlıdır (`shape =1` veya `shape = 2`). İlk olarak hangi projeksiyonın döndürüleceğini bilemezsiniz.  
  
``` sql
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
> Saklı yordamın bilgisine göre doğru türde bir Numaralandırıcı elde etmek için <xref:System.Data.Linq.IMultipleResults.GetResult%2A> deseninin kullanılması gerekir.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saklı Yordamlar](stored-procedures.md)
