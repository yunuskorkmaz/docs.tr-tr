---
title: Sayısal Dizideki Değerlerin Toplamını Hesaplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3d160e2cce5f3e0a7eea305657260b6fa4ded7fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164447"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Sayısal Dizideki Değerlerin Toplamını Hesaplama

<xref:System.Linq.Enumerable.Sum%2A>Bir dizideki sayısal değerlerin toplamını hesaplamak için işlecini kullanın.  
  
 İçindeki işlecinin aşağıdaki özelliklerine göz önünde edin `Sum` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :  
  
- Standart sorgu Işleci toplama işleci `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır olarak değerlendirilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, SQL 'in semantiği değişmeden bırakılır. Bu nedenle, `Sum` boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır yerine null olarak değerlendirilir.  
  
- Ara sonuçlarda SQL sınırlamaları, içindeki toplamalar için geçerlidir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . 32 bitlik tamsayı miktarları toplamı 64 bit sonuçlar kullanılarak hesaplanmaz ve çevirisi için taşma oluşabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Sum` . Bu olasılık, standart sorgu Işleci uygulamasının karşılık gelen bellek içi sıra için taşmaya neden olmaması durumunda bile vardır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, tablosundaki tüm siparişlerin toplam Navlun düzeyini bulur `Order` .  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `64942.6900` .  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, tüm ürünlerin sırasıyla toplam birim sayısını bulur.  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `780` .  
  
 `short`Türleri (örneğin, `UnitsOnOrder` ), `Sum` kısa türler için aşırı yüklemesi olmadığından, tür atamalısınız.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](aggregate-queries.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
