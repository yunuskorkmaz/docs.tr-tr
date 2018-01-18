---
title: "Yerel yöntem çağrıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d652072d5f2e0e0cfc74d627b573389864bca9dc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="local-method-calls"></a>Yerel yöntem çağrıları
Yerel yöntem çağrısı nesne modeli içindeki yürütülen biridir. Uzak yöntem çağırma biridir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL dönüşür ve yürütme için veritabanı altyapısı iletir. Yerel yöntem çağrılarını gerekiyor zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL çağrısından çeviremez. Aksi halde, bir <xref:System.InvalidOperationException> oluşturulur.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnekte, bir `Order` sınıfı, Northwind örnek veritabanı Siparişler tablosuna eşlendi. Yerel örnek yöntemi sınıfı eklendi.  
  
 Sorgu 1 ' için oluşturucu `Order` sınıfı yerel olarak yürütülür. İçinde 2 ise sorgu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilemedi çalıştığınız `LocalInstanceMethod()`SQL denemesi başarısız olur ve bir <xref:System.InvalidOperationException> özel durum. Ancak çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destek sağlayan yerel yöntem çağrıları için bir özel durum sorgu2 oluşturmayacaksa.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
