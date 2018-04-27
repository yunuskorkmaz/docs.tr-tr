---
title: Birleştirmeler ve çapraz ürün sorgularını düzenleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 468ee54b0936afcbb548249bc714ea4b04abd3de
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a>Birleştirmeler ve çapraz ürün sorgularını düzenleme
Aşağıdaki örnekler, birleştirme birden çok tablodan sonuçları gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `From` Visual Basic'te yan tümcesi (`from` yan tümcesinde C#) Londra'da müşteriler için tüm siparişleri seçmek için.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `Where` Visual Basic'te yan tümcesi (`where` yan tümcesinde C#) çıkış, stok için filtre uygulamak için `Products` , `Supplier` Amerika Birleşik Devletleri'nde olduğu.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `From` Visual Basic'te yan tümcesi (`from` yan tümcesinde C#) Ankara çalışanları için filtre ve bunların bölgeleri listesi.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) çalışanlar çiftleri için iki çalışanlar aynı olduğu ve burada bir çalışan diğer raporlar filtrelemek için `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Visual Basic örnek tüm müşteriler ve siparişler görünüyor, siparişler müşterilere eşleştirilir emin olur ve bu listedeki her müşteri için bir ilgili kişi adı sağlanır garanti eder.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her iki tabloyu iki tablolar ve projeleri sonuçlarını açıkça birleştirir.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, üç tablolar ve projeleri sonuçlarından bunların her birini açıkça birleştirir.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, elde etmek gösterilmiştir bir `LEFT OUTER JOIN` kullanarak `DefaultIfEmpty()`. `DefaultIfEmpty()` Yöntemi null değerini döndürür olduğunda hiçbir `Order` için `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek projeler bir `let` birleştirme sonucu oluşan ifade.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `join` bileşik bir anahtar ile.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl oluşturulacağını gösteren bir `join` burada sütunlardan boş değer atanabilir ve diğer değil.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
