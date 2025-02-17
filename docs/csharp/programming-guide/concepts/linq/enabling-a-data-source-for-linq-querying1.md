---
title: LINQ Sorgusu için Veri Kaynağı Etkinleştirme
description: C# ' de LINQ 'ı genişletmeyi, istemcilerin bir veri kaynağını sorgulamasını kolaylaştıran LINQ düzeninde sorgulanmasını sağlamak Için nasıl genişlettireceğinizi öğrenin.
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 84769e27e3f8b8d7ee30b79c219b180333337af9
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794835"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>LINQ Sorgusu için Veri Kaynağı Etkinleştirme

LINQ deseninin herhangi bir veri kaynağının sorgulanmasını sağlamak için LINQ genişletmek için çeşitli yollar vardır. Veri kaynağı örneğin bir veri yapısı, Web hizmeti, dosya sistemi veya veritabanı olabilir. LINQ stili, sorgunun sözdizimi ve deseninin değişmediği için, istemcilerin LINQ sorgusunun etkinleştirildiği bir veri kaynağını sorgulamasını kolaylaştırır. LINQ 'in bu veri kaynaklarına nasıl genişletibileceği yollarda şunlar yer alır:  
  
- <xref:System.Collections.Generic.IEnumerable%601>Bu türün sorgulanmasını LINQ to Objects etkinleştirmek için bir türde arabirimi uygulama.  
  
- <xref:System.Linq.Enumerable.Where%2A> <xref:System.Linq.Enumerable.Select%2A> Bu TÜRÜN özel LINQ sorgulanmasını etkinleştirmek için ve gibi bir türü genişleten standart sorgu işleci yöntemleri oluşturma.  
  
- Arabirimi uygulayan veri kaynağınız için bir sağlayıcı oluşturma <xref:System.Linq.IQueryable%601> . Bu arabirimi uygulayan bir sağlayıcı, LINQ sorgularını, örneğin Uzaktan özel bir şekilde yürütebileceği ifade ağaçları biçiminde alır.  
  
- Mevcut bir LINQ teknolojisinden yararlanan veri kaynağınız için bir sağlayıcı oluşturma. Böyle bir sağlayıcı, yalnızca sorgulamayı etkinleştirmez, aynı zamanda kullanıcı tanımlı türlere yönelik işlemleri ve eşleştirmeyi de ekler, güncelleştirir ve siler.  
  
 Bu konuda, bu seçenekler açıklanmaktadır.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Veri Kaynağınızın LINQ Sorgulamasını Etkinleştirme  
  
### <a name="in-memory-data"></a>Bellek İçi Veriler  

 Bellek içi veriler için LINQ sorgulaması sağlamanın iki yolu vardır. Veri, uygulayan bir tür ise <xref:System.Collections.Generic.IEnumerable%601> , LINQ to Objects kullanarak verileri sorgulayabilirsiniz. Arabirimi uygulayarak, yazdığınız türden numaralandırmayı etkinleştirmek mantıklı değilse <xref:System.Collections.Generic.IEnumerable%601> , LINQ standart sorgu işleci yöntemlerini bu türde tanımlayabilir veya türü GENIŞLETEN LINQ standart sorgu işleci yöntemleri oluşturabilirsiniz. Standart sorgu işleçlerinin özel uygulamaları, sonuçları döndürmek için ertelenmiş yürütme kullanmalıdır.  
  
### <a name="remote-data"></a>Uzak Veriler  

 Uzak bir veri kaynağının LINQ sorgulama özelliğinin etkinleştirilmesi için en iyi seçenek, <xref:System.Linq.IQueryable%601> arabirimini uygulamaktır. Ancak, bu, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bir veri kaynağı için gibi bir sağlayıcının genişlemesiyle farklılık gösterir.
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ Sağlayıcıları  

 Uygulayan LINQ sağlayıcıları <xref:System.Linq.IQueryable%601> karmaşıklığın yaygın olarak farklılık gösterebilir. Bu bölümde, farklı karmaşıklık düzeyleri açıklanmaktadır.  
  
 Daha az karmaşık bir `IQueryable` sağlayıcı, Web hizmeti 'nin tek bir yöntemiyle arabirim alabilir. Bu türden bir sağlayıcı, işlediği sorgularda belirli bilgiler beklediği için çok özeldir. Muhtemelen tek bir sonuç türü ortaya çıkaran kapalı bir tür sistemi vardır. Sorgunun çoğu yürütme, örneğin <xref:System.Linq.Enumerable> Standart sorgu işleçleri uygulamaları kullanılarak yerel olarak gerçekleşir. Daha az karmaşık olan bir sağlayıcı, sorguyu temsil eden ifade ağacında yalnızca bir yöntem çağrısı ifadesi inceleyebilir ve kalan sorgu mantığının başka bir yerde işlenmesine izin verebilir.  
  
 `IQueryable`Orta düzeyde karmaşıklığa sahip bir sağlayıcı, kısmen ifade eden bir sorgu diline sahip bir veri kaynağını hedefleyebilir. Bir Web hizmetini hedefliyorsa, Web hizmetinin birden fazla yöntemiyle arabirim oluşturabilir ve sorgunun sorduğu soruya göre bir çağrı yöntemi seçebilir. Orta düzeyde karmaşıklığa sahip bir sağlayıcının basit bir sağlayıcıya göre daha zengin bir tür sistemi vardır, ancak yine de sabit bir tür sistemidir. Örneğin, sağlayıcı ters çevrilebilen bire çok ilişkilerine sahip türleri kullanabilir, ancak kullanıcı tanımlı türler için eşleştirme teknolojisi sağlamaz.  
  
 Sağlayıcı gibi karmaşık bir `IQueryable` sağlayıcı, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Tüm LINQ sorgularını SQL gibi bir ifade eden sorgu diline çevirebilir. Karmaşık bir sağlayıcı, sorguda çok çeşitli soruları işleyebileceği için daha az karmaşık olan bir sağlayıcıya göre daha geneldir. Ayrıca, açık bir tür sistemine de sahiptir ve bu nedenle kullanıcı tanımlı türleri eşleştirmek için kapsamlı bir altyapı içermelidir. Karmaşık bir sağlayıcının geliştirilmesi için önemli ölçüde çaba gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
