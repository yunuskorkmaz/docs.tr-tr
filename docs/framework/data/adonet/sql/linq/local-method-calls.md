---
title: Yerel yöntem çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 249ed8425f175b80cb55289c2a7fe68742d8389c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655731"
---
# <a name="local-method-calls"></a>Yerel yöntem çağrıları
Yerel yöntem çağrısı nesne modeli içinde yürütülen biridir. Uzak yöntem çağırma biridir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL çevirir ve yürütme için veritabanı altyapısı iletir. Yerel yöntem çağrıları gereklidir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL çağrısına çeviremez. Aksi takdirde, bir <xref:System.InvalidOperationException> oluşturulur.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnekte, bir `Order` sınıfı Northwind örnek veritabanındaki tablosuna eşlendi. Yerel örnek yöntemi, sınıfa eklendi.  
  
 Sorgu 1 ' için oluşturucu `Order` sınıfı yerel olarak yürütülür. İçinde 2, sorgu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çevir denedi `LocalInstanceMethod()`SQL denemesi başarısız olur ve bir <xref:System.InvalidOperationException> özel durum. Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteği sağlayan yerel yöntem çağrıları için sorgu2 bir özel durum oluşturmaz.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
