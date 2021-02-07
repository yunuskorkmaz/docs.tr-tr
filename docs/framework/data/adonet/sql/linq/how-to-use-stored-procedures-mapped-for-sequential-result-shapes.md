---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sıralı sonuç şekilleri için eşlenmiş saklı yordamları kullanma'
title: 'Nasıl yapılır: Sıralı Sonuç Şekilleri İçin Eşlenmiş Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 3b5791875a7beb5a0c702e787e775cd528ab2517
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738773"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Nasıl yapılır: Sıralı Sonuç Şekilleri İçin Eşlenmiş Saklı Yordamlar Kullanma

Bu tür bir saklı yordam birden fazla sonuç şekli oluşturabilir, ancak sonuçların döndürüldüğü sırayı bilirsiniz. Bu senaryoya, döndürmeyen diziyi bildiğiniz senaryolarla kontrast. Daha fazla bilgi için bkz. [nasıl yapılır: birden çok sonuç şekli Için eşlenmiş saklı yordamları kullanma](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Örnek  

 Ardışık olarak birden çok sonuç şekli döndüren saklı yordamın T-SQL ' i aşağıda verilmiştir:  
  
```sql
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

- [Saklı yordamlar](stored-procedures.md)
