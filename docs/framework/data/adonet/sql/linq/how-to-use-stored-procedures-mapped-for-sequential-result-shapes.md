---
title: 'Nasıl yapılır: Sıralı sonuç şekilleri için eşlenmiş saklı yordamlar kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 296870029d2329640466b3a540e9057738173aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495662"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Nasıl yapılır: Sıralı sonuç şekilleri için eşlenmiş saklı yordamlar kullanma
Bu tür bir saklı yordam birden çok sonuç şekli oluşturabilirsiniz, ancak bildiğiniz hangi sırayla sonuçlar döndürülür. Bu senaryo, burada bir dizi döndürür bilmediğiniz senaryo ile karşılaştırın. Daha fazla bilgi için [nasıl yapılır: Birden çok sonuç şekli için eşlenmiş saklı yordamlar kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Örnek  
 T-SQL birden çok sonuç şekli sıralı olarak döndüren bir saklı yordam şöyledir:  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Örnek  
 Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
