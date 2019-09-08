---
title: İlişkilerde Sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: be0aea66f0923b8b353f42cecc9360731efc7bb9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792849"
---
# <a name="querying-across-relationships"></a>İlişkilerde Sorgulama
Sınıf tanımlarınızdaki diğer nesne veya diğer nesne koleksiyonları için başvurular doğrudan veritabanındaki yabancı anahtar ilişkilerine karşılık gelir. Bu ilişkileri kullanarak sorgulama özelliklerine erişin ve bir nesneden diğerine gidebilirsiniz. Bu erişim işlemleri, eşdeğer SQL 'de daha karmaşık birleştirmeler veya bağıntılı alt sorgular için çeviri yapar.  
  
 Örneğin, aşağıdaki sorgu, sonuçları yalnızca Londra 'da bulunan müşterilere yönelik siparişlerle sınırlamak için siparişlerden müşterilere gider.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 İlişki özellikleri yoksa, aşağıdaki kodda olduğu gibi bunları SQL sorgusunda yaptığınız gibi, *birleşim*olarak el ile yazmanız gerekir:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 *İlişki* özelliğini, bu belirli ilişkiyi bir kez tanımlamak için kullanabilirsiniz. Daha sonra daha kullanışlı bir nokta söz dizimini kullanabilirsiniz. Ancak, etki alanına özgü nesne modelleri genellikle hiyerarşiler veya grafikler olarak tanımlandığından ilişki özellikleri daha önemlisi vardır. Programdığı nesneler diğer nesnelere başvurmuş. Nesne-nesne ilişkilerinin, veritabanlarındaki yabancı anahtar stilli ilişkilerine karşılık geldiği bir rastlantı yalnızca bir gününüz. Özellik erişimi daha sonra birleştirmeleri yazmak için kullanışlı bir yol sağlar.  
  
 Bu konuda açıklandığı gibi, ilişki özellikleri sorgunun bir parçası olarak bir sorgunun sonuçlar tarafında daha önemlidir. Sorgu belirli bir müşteri hakkında veri aldıktan sonra, sınıf tanımı müşterilerin siparişlerinin olduğunu gösterir. Diğer bir deyişle, belirli bir müşterinin `Orders` özelliğinin bu müşterinin tüm siparişleriyle doldurulmuş bir koleksiyon olmasını bekler. Bu şekilde, bu şekilde sınıfları tanımlayarak bildirdiğiniz sözleşmenin olması gerekir. Sorgu sipariş istemese de, bu sipariþlerinizi görmeyi düşünüyorsunuz. Nesne modelinizi, ilgili nesneleri hemen kullanılabilir olan veritabanının bellek içi uzantısı olduğunu bir Yanıan koruyacak şekilde bekleolursunuz.  
  
 Artık ilişkilerimize sahip olduğunuza göre, sınıflarınızda tanımlanan ilişki özelliklerine başvurarak sorgu yazabilirsiniz. Bu ilişki başvuruları, veritabanındaki yabancı anahtar ilişkilerine karşılık gelir. Bu ilişkileri kullanan işlemler, eşdeğer SQL 'de daha karmaşık birleştirmeler için çeviri yapar. Bir ilişki tanımladığınız sürece ( <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliğini kullanarak), içinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]açık bir katılmayı kodlamamalısınız.  
  
 Bu yanılsaın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] korunmasını sağlamak için *ertelenmiş yükleme*adlı bir teknik uygular. Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
 Çiftler listesini `CustomerID` - proje için aşağıdaki SQL sorgusunu göz önünde bulundurun: `OrderID`  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Kullanarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]aynı sonuçları elde etmek için, `Customer` sınıfında zaten var olan `Orders` Özellik başvurusunu kullanırsınız. Başvuru, aşağıdaki kodda olduğu gibi sorguyu yürütmek ve `OrderID` çiftleri `CustomerID` - proje için gerekli bilgileri sağlar: `Orders`  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Ayrıca, tersten de yapabilirsiniz. Diğer bir deyişle, ilişkili `Orders` `Customer` nesneyle ilgili bilgilere erişmek `Customer` için ilişki başvurusunu sorgulayabilir ve kullanabilirsiniz. Aşağıdaki kod, önceki ile aynı `CustomerID` - `OrderID` `Orders` çiftleri`Customers`, ancak bunun yerine sorgulanarak bu süreyi sorgular.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
