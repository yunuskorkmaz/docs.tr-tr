---
title: İlişkilerde Sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 2e1cf9efcf47fc70421c64541aead5fb36d8c9d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916779"
---
# <a name="querying-across-relationships"></a>İlişkilerde Sorgulama
Diğer nesne veya koleksiyonlar, sınıf tanımlarındaki diğer nesnelerin başvuruları doğrudan veritabanında yabancı anahtar ilişkileri karşılık gelir. İlişki özelliklerine erişmek ve bir nesneden diğerine gitmek için nokta gösterimi kullanılarak sorguladığınızda, bu ilişkileri kullanabilirsiniz. Bu erişim işlemleri daha karmaşık birleştirmelerden veya eşdeğer SQL bağıntılı alt sorgularda çevir.  
  
 Örneğin, aşağıdaki sorguyu yalnızca Londra'da bulunan müşteriler için siparişleri için sonuçları kısıtlamak için bir yol olarak müşterilere siparişleri gider.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 İlişki özellikleri mevcut değilse bunları yazmanız gerekir el ile olarak *birleştirmeler*, aşağıdaki kodda gösterildiği gibi bir SQL sorgusunda yaptığınız gibi:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Kullanabileceğiniz *ilişki* özelliği bir kez bu belirli bir ilişki tanımlamak için. Ardından, daha kolay nokta sözdizimini kullanabilirsiniz. Ancak, etki alanına özgü nesne modellerini genellikle hiyerarşileri veya grafikleri tanımlandığından ilişki özelliklerini daha da önemlisi mevcut. Karşı program nesneleri diğer nesnelere başvurular var. Bu nesne için nesne ilişkilerini yabancı anahtar biçimlendirilmiş ilişkileri veritabanlarındaki karşılık gelen bir mutlu rastlantı olur. Özellik erişimini ardından birleştirmeler yazmak için kullanışlı bir yol sağlar.  
  
 Bu onaylamaz, ilişki sorgunun bir parçası olarak sorgunun sonuçları tarafında daha önemli özelliklerdir. Sorgu, belirli bir müşteri hakkında veri aldığını sonra müşterilerin siparişler sahip sınıf tanımını gösterir. Diğer bir deyişle, beklediğiniz `Orders` söz konusu müşterinin tüm siparişleri doldurulur bir koleksiyon için belirli bir müşterinin özelliği. Aslında bu şekilde sınıflar tanımlayarak bildirilen sözleşme olmasıdır. Sorgu siparişler istemedi bile siparişleri var görmeyi beklediğiniz. Veritabanı ile ilgili nesneleri hemen kullanılabilir bellek içi uzantısı olan bir görünümü korumak için nesne modeli beklediğiniz.  
  
 İlişkiler olduğuna göre sınıflarınızdaki tanımlanmış ilişki özelliklerini başvurarak sorgularınızı yazabilirsiniz. Bu ilişki başvuruları, veritabanında yabancı anahtar ilişkileri karşılık gelir. Bu ilişkiler kullanan işlemleri için daha karmaşık birleştirmeler eşdeğer SQL çevir. Bir ilişki tanımladığınız sürece (kullanarak <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği), açık bir birleştirme işleminde kod gerekmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Bu izlenimi sağlanmasına yardımcı olmak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] olarak adlandırılan tekniği uygulayan *Ertelenen yükleme*. Daha fazla bilgi için [Ertelenen hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 Proje bir listesi için aşağıdaki SQL sorgusunu göz önünde bulundurun `CustomerID` - `OrderID` çiftleri:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Kullanarak aynı sonucu elde etmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], kullandığınız `Orders` Özellik Başvurusu zaten mevcut `Customer` sınıfı. `Orders` Başvuru proje ve sorgu yürütmek için gereken bilgileri sağlayan `CustomerID` - `OrderID` çiftleri, aşağıdaki kod gibi:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Bu durumun tersi de yapabilirsiniz. Diğer bir deyişle, sorgu `Orders` ve kendi `Customer` ilişkili hakkında bilgilere erişmek için ilişki başvuru `Customer` nesne. Aşağıdaki kod aynı projeleri `CustomerID` - `OrderID` sorgulayarak önce olduğu gibi ancak bu kez çiftlerini `Orders` yerine `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
