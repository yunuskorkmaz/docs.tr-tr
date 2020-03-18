---
title: LINQ Sorgusu için Veri Kaynağı Etkinleştirme
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 9a143f0da74d4e91ef697f468d7fda225e75245b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635775"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>LINQ Sorgusu için Veri Kaynağı Etkinleştirme
Linq deseni içinde herhangi bir veri kaynağının sorgulanmasını sağlamak için LINQ'yi genişletmenin çeşitli yolları vardır. Veri kaynağı örneğin bir veri yapısı, Web hizmeti, dosya sistemi veya veritabanı olabilir. LINQ deseni, sorgunun sözdizimi ve deseni değişmediği için, istemcilerin LINQ sorgusunun etkin olduğu bir veri kaynağını sorgulamasını kolaylaştırır. LINQ'nin bu veri kaynaklarına nasıl genişletilebildiği aşağıdakileri içerir:  
  
- Bu tür <xref:System.Collections.Generic.IEnumerable%601> nesneleri sorgulayan LINQ etkinleştirmek için bir tür arabirimi uygulama.  
  
- Bu tür özel LINQ sorgusu etkinleştirmek için, bir tür genişletmek gibi <xref:System.Linq.Enumerable.Where%2A> standart <xref:System.Linq.Enumerable.Select%2A> sorgu işleci yöntemleri oluşturma.  
  
- <xref:System.Linq.IQueryable%601> Arabirimi uygulayan veri kaynağınız için bir sağlayıcı oluşturma. Bu arabirimi uygulayan bir sağlayıcı, örneğin uzaktan, özel bir şekilde yürütebileceği ifade ağaçları şeklinde LINQ sorguları alır.  
  
- Veri kaynağınız için varolan bir LINQ teknolojisinden yararlanan bir sağlayıcı oluşturma. Böyle bir sağlayıcı, yalnızca sorgulamayı etkinleştirmez, aynı zamanda kullanıcı tanımlı türlere yönelik işlemleri ve eşleştirmeyi de ekler, güncelleştirir ve siler.  
  
 Bu konuda, bu seçenekler açıklanmaktadır.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Veri Kaynağınızın LINQ Sorgulamasını Etkinleştirme  
  
### <a name="in-memory-data"></a>Bellek İçi Veriler  
 LINQ bellek içi verilerin sorgulanmasını etkinleştirmenin iki yolu vardır. Veriler uygulayan bir <xref:System.Collections.Generic.IEnumerable%601>türdeyse, Nesnelere LINQ kullanarak verileri sorgulayabilirsiniz. <xref:System.Collections.Generic.IEnumerable%601> Arabirimi uygulayarak türünüzün numaralandırmasını etkinleştirmek mantıklı değilse, bu türde LINQ standart sorgu işleci yöntemlerini tanımlayabilir veya türü genişleten LINQ standart sorgu işleci yöntemlerini oluşturabilirsiniz. Standart sorgu işleçlerinin özel uygulamaları, sonuçları döndürmek için ertelenmiş yürütme kullanmalıdır.  
  
### <a name="remote-data"></a>Uzak Veriler  
 Uzak bir veri kaynağının LINQ sorgusunu etkinleştirmek için <xref:System.Linq.IQueryable%601> en iyi seçenek arabirimi uygulamaktır. Ancak, bu, bir veri kaynağı [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] gibi bir sağlayıcı genişletme farklıdır. Visual Studio 2008'de varolan [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]LINQ teknolojilerini diğer veri kaynağı türlerine genişletmek için sağlayıcı modelleri bulunmamaktadır.
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ Sağlayıcıları  
 Uygulayan <xref:System.Linq.IQueryable%601> LINQ sağlayıcıları karmaşıklıklarında büyük farklılıklar gösterebilir. Bu bölümde, farklı karmaşıklık düzeyleri açıklanmaktadır.  
  
 Daha az `IQueryable` karmaşık bir sağlayıcı, tek bir Web hizmeti yöntemiyle arabirim yapabilir. Bu türden bir sağlayıcı, işlediği sorgularda belirli bilgiler beklediği için çok özeldir. Muhtemelen tek bir sonuç türü ortaya çıkaran kapalı bir tür sistemi vardır. Sorgunun yürütülmesinin çoğu, örneğin standart sorgu işleçlerinin <xref:System.Linq.Enumerable> uygulamalarını kullanarak yerel olarak gerçekleşir. Daha az karmaşık olan bir sağlayıcı, sorguyu temsil eden ifade ağacında yalnızca bir yöntem çağrısı ifadesi inceleyebilir ve kalan sorgu mantığının başka bir yerde işlenmesine izin verebilir.  
  
 Orta `IQueryable` karmaşıklık sağlayıcısı, kısmen anlamlı sorgu dili olan bir veri kaynağını hedefleyebilir. Bir Web hizmetini hedefliyorsa, Web hizmetinin birden fazla yöntemiyle arabirim oluşturabilir ve sorgunun sorduğu soruya göre bir çağrı yöntemi seçebilir. Orta düzeyde karmaşıklığa sahip bir sağlayıcının basit bir sağlayıcıya göre daha zengin bir tür sistemi vardır, ancak yine de sabit bir tür sistemidir. Örneğin, sağlayıcı ters çevrilebilen bire çok ilişkilerine sahip türleri kullanabilir, ancak kullanıcı tanımlı türler için eşleştirme teknolojisi sağlamaz.  
  
 Sağlayıcı `IQueryable` gibi karmaşık bir sağlayıcı, tüm LINQ sorgularını SQL gibi etkileyici bir sorgu diline çevirebilir. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Karmaşık bir sağlayıcı, sorguda çok çeşitli soruları işleyebileceği için daha az karmaşık olan bir sağlayıcıya göre daha geneldir. Ayrıca, açık bir tür sistemine de sahiptir ve bu nedenle kullanıcı tanımlı türleri eşleştirmek için kapsamlı bir altyapı içermelidir. Karmaşık bir sağlayıcının geliştirilmesi için önemli ölçüde çaba gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Nesnelere LINQ (C#)](./linq-to-objects.md)
