---
title: LINQ Querying2 için veri kaynağını etkinleştirme
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: 312a880158e4d9254d6ead81538dc9a17e5c31b0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "68959781"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>LINQ Sorgusu için Veri Kaynağı Etkinleştirme

Herhangi bir veri kaynağının, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] düzende sorgulanmasını sağlamak için genişlemenin çeşitli yolları vardır. Veri kaynağı örneğin bir veri yapısı, Web hizmeti, dosya sistemi veya veritabanı olabilir. Bu model, sorgunun sözdizimi ve deseninin değişmediği [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] için, istemcilerin sorgulama etkinleştirildiği bir veri kaynağını sorgulamasını kolaylaştırır. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Bu veri kaynaklarına genişletilebilen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yollar şunlardır:

- Bu türün sorgulanmasına olanak tanımak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] için arabirimbirtüriçindeuygulama.<xref:System.Collections.Generic.IEnumerable%601>

- Bu türün özel <xref:System.Linq.Enumerable.Where%2A> <xref:System.Linq.Enumerable.Select%2A> sorgulanmasınıetkinleştirmekiçinvegibibirtürügenişletenstandartsorgu[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işleci yöntemleri oluşturma.

- <xref:System.Linq.IQueryable%601> Arabirimi uygulayan veri kaynağınız için bir sağlayıcı oluşturma. Bu arabirimi uygulayan bir sağlayıcı, sorguları [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , örneğin Uzaktan özel bir şekilde yürütebileceği ifade ağaçları biçiminde alır.

- Veri kaynağınız için mevcut [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir teknolojinin avantajlarından yararlanan bir sağlayıcı oluşturma. Böyle bir sağlayıcı, yalnızca sorgulamayı etkinleştirmez, aynı zamanda kullanıcı tanımlı türlere yönelik işlemleri ve eşleştirmeyi de ekler, güncelleştirir ve siler.

Bu konuda, bu seçenekler açıklanmaktadır.

## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Veri Kaynağınızın LINQ Sorgulamasını Etkinleştirme

### <a name="in-memory-data"></a>Bellek İçi Veriler
 Bellek içi verilerin sorgulanmasını mümkün kılmak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] için iki yol vardır. Veri, uygulayan <xref:System.Collections.Generic.IEnumerable%601>bir tür ise, nesneleri kullanarak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] verileri sorgulayabilirsiniz. <xref:System.Collections.Generic.IEnumerable%601> Arabirimi uygulayarak, yazdığınız türden numaralandırmayı etkinleştirmek mantıklı değilse, bu türde standart sorgu işleci yöntemleri tanımlayabilir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veya türü genişleten standart sorgu işleci yöntemleri oluşturabilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] . Standart sorgu işleçlerinin özel uygulamaları, sonuçları döndürmek için ertelenmiş yürütme kullanmalıdır.

### <a name="remote-data"></a>Uzak Veriler
 Uzak bir veri kaynağının sorgulanmasını etkinleştirmek [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] için en iyi seçenek, <xref:System.Linq.IQueryable%601> arabirimini uygulamaktır. Ancak, bu, bir veri kaynağı için gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bir sağlayıcının genişlemesiyle farklılık gösterir. Visual Studio 2008 ' de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], diğer veri kaynağı türlerine gibi mevcut teknolojileri genişletmek için hiçbir sağlayıcı modeli mevcuttur.

## <a name="iqueryable-linq-providers"></a>IQueryable LINQ Sağlayıcıları
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]uygulayan <xref:System.Linq.IQueryable%601> sağlayıcılar, karmaşıklığının büyük ölçüde farklılık gösterebilir. Bu bölümde, farklı karmaşıklık düzeyleri açıklanmaktadır.

 Daha az karmaşık `IQueryable` bir sağlayıcı, Web hizmeti 'nin tek bir yöntemiyle arabirim alabilir. Bu türden bir sağlayıcı, işlediği sorgularda belirli bilgiler beklediği için çok özeldir. Muhtemelen tek bir sonuç türü ortaya çıkaran kapalı bir tür sistemi vardır. Sorgunun çoğu yürütme, örneğin standart sorgu işleçleri <xref:System.Linq.Enumerable> uygulamaları kullanılarak yerel olarak gerçekleşir. Daha az karmaşık olan bir sağlayıcı, sorguyu temsil eden ifade ağacında yalnızca bir yöntem çağrısı ifadesi inceleyebilir ve kalan sorgu mantığının başka bir yerde işlenmesine izin verebilir.

 Orta düzeyde karmaşıklığa sahip bir sağlayıcı,kısmenifadeedenbirsorgudilinesahipbirverikaynağınıhedefleyebilir.`IQueryable` Bir Web hizmetini hedefliyorsa, Web hizmetinin birden fazla yöntemiyle arabirim oluşturabilir ve sorgunun sorduğu soruya göre bir çağrı yöntemi seçebilir. Orta düzeyde karmaşıklığa sahip bir sağlayıcının basit bir sağlayıcıya göre daha zengin bir tür sistemi vardır, ancak yine de sabit bir tür sistemidir. Örneğin, sağlayıcı ters çevrilebilen bire çok ilişkilerine sahip türleri kullanabilir, ancak kullanıcı tanımlı türler için eşleştirme teknolojisi sağlamaz.

 Sağlayıcı gibi `IQueryable` karmaşık bir sağlayıcı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , tüm sorguları SQL gibi bir ifade eden sorgu diline çevirebilir. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Karmaşık bir sağlayıcı, sorguda çok çeşitli soruları işleyebileceği için daha az karmaşık olan bir sağlayıcıya göre daha geneldir. Ayrıca, açık bir tür sistemine de sahiptir ve bu nedenle kullanıcı tanımlı türleri eşleştirmek için kapsamlı bir altyapı içermelidir. Karmaşık bir sağlayıcının geliştirilmesi için önemli ölçüde çaba gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
