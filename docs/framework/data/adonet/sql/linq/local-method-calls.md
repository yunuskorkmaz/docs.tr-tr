---
title: Yerel Yöntem Çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: ec288d5ac2f6466860362be82c619c89204e8f31
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781426"
---
# <a name="local-method-calls"></a>Yerel Yöntem Çağrıları
Yerel bir yöntem çağrısı, nesne modeli içinde yürütülür. Uzak yöntem çağrısı, SQL 'e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çeviren ve yürütme için veritabanı altyapısına ileten bir veritabanıdır. Çağrıyı SQL 'e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çeviremez yerel Yöntem çağrıları gereklidir. Aksi takdirde, <xref:System.InvalidOperationException> bir oluşturulur.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnekte, bir `Order` sınıf Northwind örnek veritabanındaki Orders tablosuyla eşlenir. Sınıfına bir yerel örnek yöntemi eklenmiştir.  
  
 Sorgu 1 ' de, `Order` sınıf için Oluşturucu yerel olarak yürütülür. Sorgu 2 ' de, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 'e çevrilmeye `LocalInstanceMethod()`çalıştıysanız, deneme başarısız olur ve bir <xref:System.InvalidOperationException> özel durum oluşturulur. Ancak, yerel Yöntem çağrıları için destek sağladığından,query2birözeldurumoluşturmaz.[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
