---
title: "Ertelenmiş karşı hemen yükleniyor"
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
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f40f6c3d94aeeae41c4cce00bac8de863226f287
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="deferred-versus-immediate-loading"></a>Ertelenmiş karşı hemen yükleniyor
Bir nesne için sorgularken gerçekte yalnızca istediğiniz nesnesini alın. *İlgili* nesneleri değil otomatik olarak alınan aynı anda. (Daha fazla bilgi için bkz: [sorgulama arasında ilişkiler](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Bunları erişme denemesi bunları alır bir isteği oluşturduğundan ilişkili nesneleri zaten olmayan olgu yüklenmiş göremezsiniz.  
  
 Örneğin, belirli bir sipariş kümesi için sorgu ve bir e-posta bildirimi belirli müşterilere nadiren göndermek isteyebilirsiniz. Mutlaka Başlangıçta tüm müşteri verilerine her sipariş ile almak ihtiyaç duymaz. Ek bilgi alınmasını kesinlikle zorunda kadar erteleme Ertelenen yükleme kullanabilirsiniz. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Tersi de olabilir. Aynı anda müşteri ve sipariş verilerini görüntülemek için olan bir uygulama olabilir. Her iki veri kümesini gerektiğini bildirin. Sonuçlar elde hemen sonra uygulamanızın sipariş bilgilerini her müşteri için gerekiyor. bildiğiniz. Her müşteri için siparişler için tek tek sorgular göndermeye istemezsiniz. Gerçekten istediğiniz müşterilerin birlikte sipariş verileri sağlamaktır.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Ayrıca müşteriler ve siparişler bir sorguda çapraz ürün oluşturma ve bir büyük projeksiyon olarak verilerin tüm göreli BITS alma birleştirebilirsiniz. Ancak bu sonuçları varlıklar değildir. (Daha fazla bilgi için bkz: [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)). Bu sonuçları değişti ve kalıcı tahminleri olur ancak kimlik ve olduğunu değiştirebilirsiniz, nesneleri varlıklardır. Her bir müşteri düzleştirilmiş birleştirme çıkış her sırada yinelenir gibi kötüsü, çok fazla yedek veri alma.  
  
 Gerçekten ihtiyacınız, aynı anda bir dizi ilgili nesneyi almak için bir yoldur. Hiçbir zaman fazla veya az kullanım amacınız için gerekli olandan alma böylece bir grafik sonuçları bir bölümünü kümesidir. Bu amaçla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sağlar <xref:System.Data.Linq.DataLoadOptions> nesne modeli bölge hemen yüklenmesi için. Yöntemler şunlardır:  
  
-   <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Hemen ana hedefe ilgili verileri yüklemek için yöntem.  
  
-   <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Yöntemine filtre nesneleri için belirli bir ilişkisi alınamadı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
