---
title: 'Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 342583cdbf6a1501f1bc70c6a9be5d7009c390eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940248"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme
Ana Hedefinizdeki ilgili verilerin aynı anda alınması gereken verileri belirtmek için yönteminikullanın.<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Örneğin, müşterilerin siparişleriyle ilgili bilgilere ihtiyacınız olduğunu biliyorsanız, sipariş bilgilerinin Müşteri bilgileriyle aynı zamanda alındığından emin <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> olmak için kullanabilirsiniz. Bu yaklaşım, her iki bilgi kümesi için yalnızca bir seyahat veritabanına neden olur.  
  
> [!NOTE]
> Bir mimariler, müşterileri hedefleyerek siparişleri alma gibi bir büyük projeksiyon olarak bir çapraz ürün alarak, sorgunuzun ana hedefle ilgili verileri alabilirsiniz. Ancak bu yaklaşım genellikle dezavantajlara sahiptir. Örneğin, sonuçlar yalnızca tahmindir ve tarafından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]değiştirilebilecek ve kalıcı hale kullanılabilecek varlıklardır. Ve ihtiyacınız olmayan çok fazla veri alabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, Londra 'da bulunan `Orders` `Customers` tüm kullanıcılar için, sorgu yürütüldüğünde alınır. Sonuç olarak, bir `Orders` `Customer` nesnedeki özelliğe art arda erişim yeni bir veritabanı sorgusu tetiklemez.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
