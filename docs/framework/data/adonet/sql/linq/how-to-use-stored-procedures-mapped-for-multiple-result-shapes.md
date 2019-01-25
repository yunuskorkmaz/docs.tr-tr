---
title: 'Nasıl yapılır: Birden çok sonuç şekli için eşlenmiş saklı yordamlar kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 6ea318e89cf91dcbf16747117b8000dfa3f9571d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573679"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Nasıl yapılır: Birden çok sonuç şekli için eşlenmiş saklı yordamlar kullanma
Bir saklı yordam birden çok sonuç şekli döndüğünüzde dönüş türü kesin bir tek projeksiyon şekle yazılamaz. Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tüm olası yansıtma türleri oluşturabilirsiniz, siparişin bunlar döndürülecek bilemezsiniz.  
  
 Bu senaryo ile sıralı olarak birden çok sonuç şekli oluşturan saklı yordamları karşılaştırın. Daha fazla bilgi için [nasıl yapılır: Sıralı sonuç şekilleri için eşlenmiş saklı yordamlar kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 <xref:System.Data.Linq.Mapping.ResultTypeAttribute> Özniteliği, dönüş türleri yordamı döndürebilir belirtmek için birden çok sonuç türleri, saklı yordamlar için uygulanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kod örneğinde sonuç şekli girişine bağlı (`shape =1` veya `shape = 2`). Hangi projeksiyon ilk döndürülecek bilmezsiniz.  
  
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
>  Kullanmalısınız <xref:System.Data.Linq.IMultipleResults.GetResult%2A> doğru türde saklı yordamın, bilgilere dayanan bir numaralandırıcı almak için desen.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
