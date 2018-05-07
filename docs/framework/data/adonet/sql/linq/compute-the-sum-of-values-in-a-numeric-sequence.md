---
title: Bir sayısal sırada değerlerinin toplamı işlem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: d1c49d45eaf82101e57e0886af52a134d24b1651
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
