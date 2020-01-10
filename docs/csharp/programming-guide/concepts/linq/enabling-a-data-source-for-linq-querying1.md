---
title: LINQ Sorgusu için Veri Kaynağı Etkinleştirme
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 9a143f0da74d4e91ef697f468d7fda225e75245b
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635775"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>LINQ Sorgusu için Veri Kaynağı Etkinleştirme
LINQ deseninin herhangi bir veri kaynağının sorgulanmasını sağlamak için LINQ genişletmek için çeşitli yollar vardır. Veri kaynağı örneğin bir veri yapısı, Web hizmeti, dosya sistemi veya veritabanı olabilir. LINQ stili, sorgunun sözdizimi ve deseninin değişmediği için, istemcilerin LINQ sorgusunun etkinleştirildiği bir veri kaynağını sorgulamasını kolaylaştırır. LINQ 'in bu veri kaynaklarına nasıl genişletibileceği yollarda şunlar yer alır:  
  
- Bu türün LINQ to Objects sorgulanmasını etkinleştirmek için bir türde <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulama.  
  
- Türü genişleten <xref:System.Linq.Enumerable.Where%2A> ve <xref:System.Linq.Enumerable.Select%2A> gibi standart sorgu işleci yöntemleri oluşturma, bu türün özel LINQ sorgulaması sağlamak için.  
  
- Veri kaynağınız için <xref:System.Linq.IQueryable%601> arabirimini uygulayan bir sağlayıcı oluşturma. Bu arabirimi uygulayan bir sağlayıcı, LINQ sorgularını, örneğin Uzaktan özel bir şekilde yürütebileceği ifade ağaçları biçiminde alır.  
  
- Mevcut bir LINQ teknolojisinden yararlanan veri kaynağınız için bir sağlayıcı oluşturma. Böyle bir sağlayıcı, yalnızca sorgulamayı etkinleştirmez, aynı zamanda kullanıcı tanımlı türlere yönelik işlemleri ve eşleştirmeyi de ekler, güncelleştirir ve siler.  
  
 Bu konuda, bu seçenekler açıklanmaktadır.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Veri Kaynağınızın LINQ Sorgulamasını Etkinleştirme  
  
### <a name="in-memory-data"></a>Bellek İçi Veriler  
 Bellek içi veriler için LINQ sorgulaması sağlamanın iki yolu vardır. Veriler <xref:System.Collections.Generic.IEnumerable%601>uygulayan bir tür ise, LINQ to Objects kullanarak verileri sorgulayabilirsiniz. <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayarak, yazdığınız türden numaralandırmayı etkinleştirmek mantıklı değilse, LINQ standart sorgu işleci yöntemlerini bu türde tanımlayabilir veya türü genişleten LINQ standart sorgu işleci yöntemleri oluşturabilirsiniz. Standart sorgu işleçlerinin özel uygulamaları, sonuçları döndürmek için ertelenmiş yürütme kullanmalıdır.  
  
### <a name="remote-data"></a>Uzak Veriler  
 Uzak bir veri kaynağının LINQ sorgulama özelliğinin etkinleştirilmesi için en iyi seçenek <xref:System.Linq.IQueryable%601> arabirimini uygulamaktır. Ancak, bu, bir veri kaynağı için [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] gibi bir sağlayıcıyı genişletmenin bir farklılık gösterir. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]gibi var olan LINQ teknolojilerini genişletmek için hiçbir sağlayıcı modeli, Visual Studio 2008 ' de diğer veri kaynağı türlerine kullanılabilir.
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ Sağlayıcıları  
 <xref:System.Linq.IQueryable%601> uygulayan LINQ sağlayıcıları karmaşıklık bakımından çok farklılık gösterebilir. Bu bölümde, farklı karmaşıklık düzeyleri açıklanmaktadır.  
  
 Daha az karmaşık bir `IQueryable` sağlayıcı, Web hizmeti 'nin tek bir yöntemiyle arabirim alabilir. Bu türden bir sağlayıcı, işlediği sorgularda belirli bilgiler beklediği için çok özeldir. Muhtemelen tek bir sonuç türü ortaya çıkaran kapalı bir tür sistemi vardır. Sorgunun çoğu yürütme, örneğin standart sorgu işleçlerinin <xref:System.Linq.Enumerable> uygulamalarını kullanarak yerel olarak gerçekleşir. Daha az karmaşık olan bir sağlayıcı, sorguyu temsil eden ifade ağacında yalnızca bir yöntem çağrısı ifadesi inceleyebilir ve kalan sorgu mantığının başka bir yerde işlenmesine izin verebilir.  
  
 Orta düzeyde karmaşıklığa sahip bir `IQueryable` sağlayıcısı, kısmen ifade eden bir sorgu diline sahip bir veri kaynağını hedefleyebilir. Bir Web hizmetini hedefliyorsa, Web hizmetinin birden fazla yöntemiyle arabirim oluşturabilir ve sorgunun sorduğu soruya göre bir çağrı yöntemi seçebilir. Orta düzeyde karmaşıklığa sahip bir sağlayıcının basit bir sağlayıcıya göre daha zengin bir tür sistemi vardır, ancak yine de sabit bir tür sistemidir. Örneğin, sağlayıcı ters çevrilebilen bire çok ilişkilerine sahip türleri kullanabilir, ancak kullanıcı tanımlı türler için eşleştirme teknolojisi sağlamaz.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sağlayıcısı gibi karmaşık bir `IQueryable` sağlayıcı, tüm LINQ sorgularını SQL gibi bir ifade eden sorgu diline çevirebilir. Karmaşık bir sağlayıcı, sorguda çok çeşitli soruları işleyebileceği için daha az karmaşık olan bir sağlayıcıya göre daha geneldir. Ayrıca, açık bir tür sistemine de sahiptir ve bu nedenle kullanıcı tanımlı türleri eşleştirmek için kapsamlı bir altyapı içermelidir. Karmaşık bir sağlayıcının geliştirilmesi için önemli ölçüde çaba gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
