---
title: Ertelenmiş ve Hemen Yükleme Karşılaştırması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: ae20dbe557c3cf56a273556c24578056843e9af6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096998"
---
# <a name="deferred-versus-immediate-loading"></a>Ertelenmiş ve Hemen Yükleme Karşılaştırması
Bir nesne için sorgularken, yalnızca istediğiniz nesneyi gerçekten alın. *İlgili* nesneleri olmayan otomatik olarak getirilen aynı anda. (Daha fazla bilgi için [sorgulama arasında ilişkiler](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Bunları erişme denemesi bunları alır bir istek oluşturur çünkü ilgili nesneler zaten olmayan olgu yüklenmiş göremez.  
  
 Örneğin, siparişler belirli bir kümesini sorgulamak ve bir e-posta bildirimi belirli müşterilere nadiren göndermek isteyebilirsiniz. Mutlaka Başlangıçta tüm müşteri verilerine her sipariş almak zorunda kalmaz. Ertelenen yükleme kesinlikle zorunda kadar ek bilgilerin alınmasını ertelemek için kullanabilirsiniz. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Tersi de olabilir. Aynı anda müşteri ile sipariş verilerini görüntülemek için olan bir uygulama olabilir. Her iki veri kümesini gereksinim bildiğiniz. Sonuçlar elde hemen sonra uygulamanızın sipariş bilgilerini her müşteri için ihtiyaç duyduğu. bildiğiniz. Her müşteriye ait siparişlerin tek tek sorguları göndermek istemezsiniz. Müşterilerin birlikte sipariş verilerini almak için gerçekten istediğiniz olduğu.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Ayrıca müşteriler ve siparişler bir sorguda çapraz ürün oluşturma ve tüm göreli büyük bir projeksiyon olarak veri bitlerini almak katılabilirsiniz. Ancak bu sonuçları varlıkları değildir. (Daha fazla bilgi için [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)). Bu sonuçları değiştirildi ve kalıcı projeksiyonlar olacaktır ancak kimlik ve değişiklik yapabileceğiniz, sahip nesneleri varlıklardır. Her müşteri düzleştirilmiş birleştirme çıktıda her sipariş yinelenir gibi daha da kötüsü, pek çok yedekli veri alınıyor.  
  
 Gerçekten gerekenleri, aynı zamanda ilgili nesneleri kümesini almak için bir yoldur. Böylece, hiçbir zaman fazla veya az kullanım amacınız için gerekli olandan alınıyor sonuçları bir grafik bölümünü kümesidir. Bu amaçla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sağlar <xref:System.Data.Linq.DataLoadOptions> için nesne modeli, bölge ve hemen yükleme. Yöntemler şunlardır:  
  
-   <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Hemen ana hedef ilgili verileri yüklemek için yöntemi.  
  
-   <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Yöntemine filtre nesneleri için belirli bir ilişkinin alınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
