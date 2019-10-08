---
title: 'Nasıl yapılır: sıralı sonuç şekilleri için eşlenmiş saklı yordamları kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 8378a175ab2479ab9769ca08579e1c89269eaba4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003226"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Nasıl yapılır: sıralı sonuç şekilleri için eşlenmiş saklı yordamları kullanma
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

- [Saklı Yordamlar](stored-procedures.md)
