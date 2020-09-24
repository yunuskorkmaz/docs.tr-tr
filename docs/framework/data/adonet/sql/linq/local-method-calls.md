---
title: Yerel Yöntem Çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 25aded1aa961e182e8d2d472fca4c5a84b501af1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166176"
---
# <a name="local-method-calls"></a>Yerel Yöntem Çağrıları

Yerel bir yöntem çağrısı, nesne modeli içinde yürütülür. Uzak yöntem çağrısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 'e çeviren ve yürütme için veritabanı altyapısına ileten bir veritabanıdır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ÇAĞRıYı SQL 'e çeviremez yerel Yöntem çağrıları gereklidir. Aksi takdirde, bir oluşturulur <xref:System.InvalidOperationException> .  
  
## <a name="example-1"></a>Örnek 1  

 Aşağıdaki örnekte, bir `Order` sınıf Northwind örnek veritabanındaki Orders tablosuyla eşlenir. Sınıfına bir yerel örnek yöntemi eklenmiştir.  
  
 Sorgu 1 ' de, sınıf için Oluşturucu `Order` yerel olarak yürütülür. Sorgu 2 ' de, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 'e çevrilmeye çalıştıysanız `LocalInstanceMethod()` , deneme başarısız olur ve bir <xref:System.InvalidOperationException> özel durum oluşturulur. Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , yerel Yöntem çağrıları için destek sağladığından, query2 bir özel durum oluşturmaz.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
