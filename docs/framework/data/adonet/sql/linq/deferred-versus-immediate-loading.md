---
title: Ertelenmiş ve Hemen Yükleme Karşılaştırması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 4e2cb7c90eb703985cbb1b8673522a9e253564d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164304"
---
# <a name="deferred-versus-immediate-loading"></a>Ertelenmiş ve Hemen Yükleme Karşılaştırması

Bir nesne için sorgulama yaptığınızda aslında yalnızca istediğiniz nesneyi alırsınız. *İlgili* nesneler otomatik olarak aynı anda getirilmez. (Daha fazla bilgi için bkz. [Ilişkiler genelinde sorgulama](querying-across-relationships.md).) İlgili nesnelerin zaten yüklenmediğini, bunlara erişim girişimi onları alan bir istek ürettiğini göremezsiniz.  
  
 Örneğin, belirli bir sipariş kümesini sorgulamak ve sonra yalnızca belirli müşterilere bir e-posta bildirimi göndermek isteyebilirsiniz. Başlangıçta tüm müşteri verilerini her sırada almanız gerekmez. Kesin olarak yapmanız gerekmedikçe ek bilgilerin alınmasını erteleyin için ertelenmiş yüklemeyi kullanabilirsiniz. Aşağıdaki örneği inceleyin:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Tersi de doğru olabilir. Aynı anda müşteri ve sipariş verilerini görüntülemek için bir uygulamanız olabilir. Her iki veri kümesine de ihtiyacınız olduğunu bilirsiniz. Sonuçları aldığınızda, uygulamanızın her müşteri için sipariş bilgilerini ihtiyaçlarını öğrenirsiniz. Her müşteri için ayrı ayrı sorgular göndermek istemezsiniz. Gerçekten istediğiniz gibi, müşteri ile sipariş verilerini almak önemlidir.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Ayrıca, bir sorgudaki müşterilere ve siparişlere, çapraz ürün oluşturarak ve tüm göreli veri bitlerini tek bir büyük projeksiyon olarak alarak katabilirsiniz. Ancak bu sonuçlar varlık değildir. (Daha fazla bilgi için, [LINQ to SQL nesne modeline](the-linq-to-sql-object-model.md)bakın). Varlıklar, kimliği olan ve değiştiremeyeceğiniz olan nesnelerdir. bu sonuçlar, değiştirilemeyen ve kalıcı olmayan projeksiyonlar olur. Daha da kötüleşseniz bile, her müşteri düzleştirilmiş bir birleşimde her bir sıraya kadar çok sayıda gereksiz veri alırsınız.  
  
 Gerçekten ihtiyacınız olan özellikler aynı anda ilgili nesneler kümesini almanın bir yoludur. Küme, hedeflenen kullanım için gerekenden daha fazla veya daha az bir şekilde alınmamanız için bir grafiğin bir ayırıcı bölümüdür. Bu amaçla, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataLoadOptions> nesne modelinizdeki bir bölgenin hemen yüklenmesini sağlar. Yöntemler şunlardır:  
  
- <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>Ana hedefle ilgili verileri hemen yüklemek için yöntemi.  
  
- <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A>Belirli bir ilişki için alınan nesneleri filtrelemek için yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
