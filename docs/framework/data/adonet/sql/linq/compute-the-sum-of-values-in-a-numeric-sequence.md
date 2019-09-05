---
title: Sayısal Dizideki Değerlerin Toplamını Hesaplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247922"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Sayısal Dizideki Değerlerin Toplamını Hesaplama
Bir dizideki sayısal değerlerin toplamını hesaplamak için işlecinikullanın.<xref:System.Linq.Enumerable.Sum%2A>  
  
 `Sum` İçindeki[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]işlecinin aşağıdaki özelliklerine göz önünde edin:  
  
- Standart sorgu işleci toplama işleci `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır olarak değerlendirilir. ' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, SQL 'in semantiği değişmeden bırakılır. Bu nedenle, `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır yerine null olarak değerlendirilir.  
  
- Ara sonuçlarda SQL sınırlamaları, içindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]toplamalar için geçerlidir. 32 bitlik tamsayı miktarları toplamı 64 bit sonuçlar kullanılarak hesaplanmaz ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Sum`çevirisi için taşma oluşabilir. Bu olasılık, standart sorgu Işleci uygulamasının karşılık gelen bellek içi sıra için taşmaya neden olmaması durumunda bile vardır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Order` tablosundaki tüm siparişlerin toplam Navlun düzeyini bulur.  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm ürünlerin sırasıyla toplam birim sayısını bulur.  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `780`.  
  
 Türleri (örneğin,) `short` `Sum` , `UnitsOnOrder`kısa türler için aşırı yüklemesi olmadığından, tür atamalısınız.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](aggregate-queries.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
