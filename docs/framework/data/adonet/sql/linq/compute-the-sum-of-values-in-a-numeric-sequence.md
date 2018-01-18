---
title: "Bir sayısal sırada değerlerinin toplamı işlem"
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
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 547d9f245d41fac2e2d65877ddbb2a8660d73c42
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Bir sayısal sırada değerlerinin toplamı işlem
Kullanım <xref:System.Linq.Enumerable.Sum%2A> bir sırada sayısal değerlerinin toplamı işlem işleci.  
  
 Aşağıdaki özellikleri Not `Sum` işlecinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Standart sorgu işleci Toplama işleci `Sum` için boş bir dizi veya yalnızca null içeren bir dizi sıfır değerlendirir. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değişmez. Bu nedenle, `Sum` null yerine sıfır yalnızca null içeren bir dizi veya boş bir dizi için değerlendirir.  
  
-   Ara sonuçların SQL sınırlamalar uygulanır Toplamaların [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. 32 bit tamsayı miktarların toplamı hesaplanan 64-bit sonuçları kullanarak ve taşma için oluşabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilmesi `Sum`. Standart sorgu işleci uygulama karşılık gelen bellek içi dizisi taşma neden olmaz olsa bile bu olasılığı bulunmaktadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tüm siparişler, toplam nakliye bulur `Order` tablo.  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm ürünleri için sipariş birimlerin toplam sayısını bulur.  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `780`.  
  
 Cast gerekir Not `short` türleri (örneğin, `UnitsOnOrder`) çünkü `Sum` kısa türleri için hiçbir aşırı yüklemesi vardır.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Toplu Sorgular](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
