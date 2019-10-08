---
title: İlişkilerde Sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 1675e4c6a610373e1c981b383ae0229739d96dd0
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003323"
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
  
 Bu konuda açıklandığı gibi, ilişki özellikleri sorgunun bir parçası olarak bir sorgunun sonuçlar tarafında daha önemlidir. Sorgu belirli bir müşteri hakkında veri aldıktan sonra, sınıf tanımı müşterilerin siparişlerinin olduğunu gösterir. Diğer bir deyişle, belirli bir müşterinin `Orders` özelliğini, bu müşterinin tüm siparişleriyle doldurulmuş bir koleksiyon olacak şekilde bekleolursunuz. Bu şekilde, bu şekilde sınıfları tanımlayarak bildirdiğiniz sözleşmenin olması gerekir. Sorgu sipariş istemese de, bu sipariþlerinizi görmeyi düşünüyorsunuz. Nesne modelinizi, ilgili nesneleri hemen kullanılabilir olan veritabanının bellek içi uzantısı olduğunu bir Yanıan koruyacak şekilde bekleolursunuz.  
  
 Artık ilişkilerimize sahip olduğunuza göre, sınıflarınızda tanımlanan ilişki özelliklerine başvurarak sorgu yazabilirsiniz. Bu ilişki başvuruları, veritabanındaki yabancı anahtar ilişkilerine karşılık gelir. Bu ilişkileri kullanan işlemler, eşdeğer SQL 'de daha karmaşık birleştirmeler için çeviri yapar. Bir ilişki tanımladığınız sürece (<xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliğini kullanarak), [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ' de açık bir katılmayı kodlamamalısınız.  
  
 Bu yanılsaın sağlanmasına yardımcı olmak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], *ertelenmiş yükleme*adlı bir teknik uygular. Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
 @No__t-0 @ no__t-1 @ no__t-2 çiftlerinin bir listesini proje için aşağıdaki SQL sorgusunu göz önünde bulundurun:  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 @No__t-0 kullanarak aynı sonuçları elde etmek için `Customer` sınıfında zaten var olan `Orders` Özellik başvurusunu kullanırsınız. @No__t-0 başvurusu, aşağıdaki kodda olduğu gibi sorguyu yürütmek ve `CustomerID` @ no__t-2 @ no__t-3 çiftlerini proje yapmak için gerekli bilgileri sağlar:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Ayrıca, tersten de yapabilirsiniz. Diğer bir deyişle, `Orders` ' ı sorgulayabilir ve `Customer` ilişki başvurusunu kullanarak ilişkili `Customer` nesnesi hakkındaki bilgilere erişebilirsiniz. Aşağıdaki kod, `CustomerID` @ no__t-1 @ no__t-2 çiftlerini daha önce olduğu gibi, ancak bu kez `Customers` yerine `Orders` ' i sorgulayarak.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
