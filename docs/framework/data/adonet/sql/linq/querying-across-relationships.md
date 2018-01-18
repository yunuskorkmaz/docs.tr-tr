---
title: "İlişkiler arasında sorgulama"
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
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f06297f79807a1548a6b5ac77aed45f52c8d03af
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="querying-across-relationships"></a>İlişkiler arasında sorgulama
Diğer nesne veya koleksiyonlar, sınıf tanımları diğer nesnelerin başvurular doğrudan veritabanında yabancı anahtar ilişkileri karşılık gelir. İlişki özelliklerine erişmek ve başka bir nesneden gezinmek için noktalı gösterim kullanarak sorguladığınızda, bu ilişkileri kullanabilirsiniz. Daha karmaşık birleştirmeler ya da eşdeğer SQL bağlantılı sorgularda erişim işlemlerini çevir.  
  
 Örneğin, aşağıdaki sorgu sonuçları yalnızca Londra'da bulunan müşteriler için siparişleri sınırlamak için bir yol olarak müşterilere siparişleri gider.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 İlişki özellikleri mevcut değilse bunları yazmanız gerekir el ile olarak *birleştirmeler*, aşağıdaki kod olduğu gibi SQL sorguda yaptığınız gibi:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Kullanabileceğiniz *ilişki* bir kez bu belirli ilişki tanımlamak için özellik. Ardından, daha kullanışlı nokta sözdizimini kullanabilirsiniz. Ancak etki alanına özgü nesne modelleri genellikle hiyerarşileri veya grafikleri tanımlandığından ilişki özellikleri daha da önemlisi yok. Karşı program nesneleri diğer nesnelerin referansları sahiptir. Nesne nesnesi ilişkileri veritabanları yabancı anahtar stilde ilişkilerde karşılık gelen bir mutluluk rastlantı olur. Özellik erişim sonra birleştirmeler yazmak için kolay bir yol sağlar.  
  
 Bu açısından ilişki sorgu sorgu parçası olarak sonuçları tarafındaki daha önemli özelliklerdir. Sorgu belirli bir müşteri hakkında veri aldığı sonra müşterilerin siparişleri sahip sınıf tanımını gösterir. Diğer bir deyişle, beklediğiniz `Orders` bu müşteriden emirleriyle doldurulmuş bir koleksiyonu olması için belirli bir müşteri özelliği. Bu şekilde sınıfları tanımlama tarafından bildirilen sözleşme aslında olmasıdır. Sorgu siparişleri istememiş olsa bile siparişleri var. görmeyi bekleyebilirsiniz. Veritabanı ile ilgili nesneleri hemen kullanılabilir bellek içi uzantısı olan bir görünümü korumak için nesne modeli bekler.  
  
 İlişkileri sahip olduğunuza göre sorguları, sınıflarda tanımlanan ilişki özelliklerini başvurarak yazabilirsiniz. Bu ilişki başvuruları veritabanında yabancı anahtar ilişkileri karşılık gelir. Bu ilişkileri kullanan işlemler eşdeğer SQL daha karmaşık birleşimlerde çevir. Tanımlanmış bir ilişkisi sürece (kullanarak <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği), açık bir birleştirme kod gerekmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Bu görünümü sağlanmasına yardımcı olmak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adında bir teknik uygulayan *yüklenirken ertelenmiş*. Daha fazla bilgi için bkz: [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 Proje listesi için aşağıdaki SQL sorgusunu göz önünde bulundurun `CustomerID` - `OrderID` çiftleri:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Kullanarak aynı sonuçları elde etmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], kullandığınız `Orders` özelliği başvuru zaten mevcut `Customer` sınıfı. `Orders` Başvuru sağlar sorgu ve proje yürütmek için gerekli bilgileri `CustomerID` - `OrderID` aşağıdaki kodu olduğu gibi çiftleri:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Bu durumun tersi de yapabilirsiniz. Diğer bir deyişle, sorgu `Orders` ve kendi `Customer` ilişki başvuru ilişkili ilgili bilgilere erişmek üzere `Customer` nesnesi. Aşağıdaki kodu aynı projeleri `CustomerID` - `OrderID` önceki gibi ancak bu kez sorgulayarak çiftleri `Orders` yerine `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
