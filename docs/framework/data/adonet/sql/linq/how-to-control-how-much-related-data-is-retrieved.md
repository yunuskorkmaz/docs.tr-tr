---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Ilgili verilerin ne kadar alındığını denetleme'
title: 'Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: becf1282d18d5c630da3e3be27c62ebae404d940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786049"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme

<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>Ana Hedefinizdeki ilgili verilerin aynı anda alınması gereken verileri belirtmek için yöntemini kullanın. Örneğin, müşterilerin siparişleriyle ilgili bilgilere ihtiyacınız olduğunu biliyorsanız, <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> sipariş bilgilerinin Müşteri bilgileriyle aynı zamanda alındığından emin olmak için kullanabilirsiniz. Bu yaklaşım, her iki bilgi kümesi için yalnızca bir seyahat veritabanına neden olur.  
  
> [!NOTE]
> Bir mimariler, müşterileri hedefleyerek siparişleri alma gibi bir büyük projeksiyon olarak bir çapraz ürün alarak, sorgunuzun ana hedefle ilgili verileri alabilirsiniz. Ancak bu yaklaşım genellikle dezavantajlara sahiptir. Örneğin, sonuçlar yalnızca tahmindir ve tarafından değiştirilebilecek ve kalıcı hale kullanılabilecek varlıklardır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Ve ihtiyacınız olmayan çok fazla veri alabilirsiniz.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, `Orders` `Customers` Londra 'da bulunan tüm kullanıcılar için, sorgu yürütüldüğünde alınır. Sonuç olarak, `Orders` bir nesnedeki özelliğe art arda erişim `Customer` Yeni bir veritabanı sorgusu tetiklemez.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanını Sorgulama](querying-the-database.md)
