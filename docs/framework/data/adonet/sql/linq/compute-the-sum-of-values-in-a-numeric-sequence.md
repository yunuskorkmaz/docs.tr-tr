---
title: Sayısal Dizideki Değerlerin Toplamını Hesaplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 2f66b996a0e688205d61f5fca476c0335616ee38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143578"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Sayısal Dizideki Değerlerin Toplamını Hesaplama
Kullanım <xref:System.Linq.Enumerable.Sum%2A> sıralı sayısal değerlerin toplamını hesaplamak için işleci.  
  
 Aşağıdaki özellikleri Not `Sum` işlecinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Standart sorgu işleci Toplama işleci `Sum` sıfıra boş bir dizi veya yalnızca null içeren bir dizi olarak değerlendirilir. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değişmez. Bu nedenle, `Sum` yerine null yalnızca null içeren bir dizi veya boş bir dizi için sıfır olarak değerlendirilir.  
  
-   Toplamalar Ara sonuçlar SQL sınırlamalar uygulanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. 32 bit tamsayı miktarlar toplamı, 64-bit sonuçları kullanarak değil hesaplanır ve taşma için meydana gelebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi `Sum`. Standart sorgu işleci uygulaması karşılık gelen bir bellek içi dizisi taşmaya neden olmaz olsa bile bu olasılığı bulunmaktadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tüm siparişleri toplam navlun bulur `Order` tablo.  
  
 Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm ürünler için sipariş toplam birim sayısını bulur.  
  
 Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `780`.  
  
 Dönüştürmelisiniz Not `short` türleri (örneğin, `UnitsOnOrder`) çünkü `Sum` kısa türleri için hiçbir aşırı yüklemesi vardır.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
