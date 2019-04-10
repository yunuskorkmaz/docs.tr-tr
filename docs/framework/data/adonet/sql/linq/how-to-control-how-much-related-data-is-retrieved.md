---
title: 'Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: dd59c09185eab003274614dcc30393b060e6b7c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215449"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme
Kullanım <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> ilgili ana hedefiniz için hangi verileri belirtmek için yöntem aynı zamanda alınan. Örneğin, müşteri siparişlerinin hakkında bilgi gerekir biliyorsanız, kullanabileceğiniz <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> sipariş bilgileri, aynı zamanda müşteri bilgileri alınır emin olmak için. Bu yaklaşım yalnızca bir dönüş içinde iki bilgi veritabanına sonuçlanır.  
  
> [!NOTE]
>  Müşteriler hedeflediğinizde siparişleri alma gibi bir büyük projeksiyon olarak çapraz ürün alarak sorgunuzun ana hedef ilgili veri alabilir. Ancak, bu yaklaşım genellikle dezavantajları vardır. Örneğin, tahminler ve olmayan değiştirilebilir ve tarafından kalıcı varlıklar sonucu olan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Ve çok sayıda gereksinim duymadığınız veriden alma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, tüm `Orders` tüm `Customers` Londra'da bulunan alınır sorgu yürütüldüğünde. Sonuç olarak, art arda gelen erişimi `Orders` özelliği bir `Customer` nesne yeni bir veritabanı sorgusu tetiklemez.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
