---
title: Veri kaynağı için LINQ Querying1 etkinleştirme
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 5b67995f40bc0cb703003aa80b511268f21da8b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339702"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>LINQ Sorgusu için Veri Kaynağı Etkinleştirme
Genişletmek için çeşitli yolları vardır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] içinde Sorgulanacak herhangi bir veri kaynağı etkinleştirmek için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] düzeni. Veri kaynağı örneğin bir veri yapısı, Web hizmeti, dosya sistemi veya veritabanı olabilir. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Düzeni istemcilerin bir veri kaynağı için sorgu kolaylaştırır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgulama etkin olduğunda, sözdizimi ve sorgu modelini değiştirmez çünkü. Hangi yollarla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Genişletilebilir bu veri kaynakları şunları içerir:  
  
-   Uygulama <xref:System.Collections.Generic.IEnumerable%601> etkinleştirmek için bir tür arabiriminde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bu tür nesneleri sorgulamak için.  
  
-   Standart sorgu işleci yöntemleri gibi oluşturma <xref:System.Linq.Enumerable.Where%2A> ve <xref:System.Linq.Enumerable.Select%2A> özel etkinleştirmek için bir tür genişletmek [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] türü sorgulama.  
  
-   Bir sağlayıcı uygular, veri kaynağı için oluşturma <xref:System.Linq.IQueryable%601> arabirimi. Bu arabirimi gerçekleştiren bir sağlayıcı alır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özel bir biçimde örneğin uzaktan çalıştırmak ifade ağaçları biçiminde sorgular.  
  
-   Varolan yararlanır veri kaynağınız için bir sağlayıcı oluşturma [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] teknolojisi. Böyle bir sağlayıcı, yalnızca sorgulamayı etkinleştirmez, aynı zamanda kullanıcı tanımlı türlere yönelik işlemleri ve eşleştirmeyi de ekler, güncelleştirir ve siler.  
  
 Bu konuda, bu seçenekler açıklanmaktadır.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Veri Kaynağınızın LINQ Sorgulamasını Etkinleştirme  
  
### <a name="in-memory-data"></a>Bellek İçi Veriler  
 İki yolla etkinleştirebilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bellek içi veri sorgulama. Veri uygulayan bir tür ise <xref:System.Collections.Generic.IEnumerable%601>, kullanarak verileri sorgulayabilir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesnelere. Bunu uygulayarak türünüz numaralandırması etkinleştirmek için anlamsız varsa <xref:System.Collections.Generic.IEnumerable%601> arabirimi, tanımlayabilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart oluşturmak veya sorguyu türü işleci yöntemleri [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] türü genişletmek standart sorgu işleci yöntemleri. Standart sorgu işleçlerinin özel uygulamaları, sonuçları döndürmek için ertelenmiş yürütme kullanmalıdır.  
  
### <a name="remote-data"></a>Uzak Veriler  
 Etkinleştirme için en iyi seçenek [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] uzak veri kaynağını sorgulaması olduğu uygulamak için <xref:System.Linq.IQueryable%601> arabirimi. Ancak, bu sağlayıcı gibi genişletme farklıdır [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bir veri kaynağı için. Varolan genişletmek için hiçbir sağlayıcı modeli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] teknolojileri gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], veri kaynağının diğer türleri kullanılabilir [!INCLUDE[vs_orcas_long](~/includes/vs-orcas-long-md.md)].  
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ Sağlayıcıları  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] uygulayan sağlayıcılar <xref:System.Linq.IQueryable%601> kendi karmaşıklık yaygın olarak değişebilir. Bu bölümde, farklı karmaşıklık düzeyleri açıklanmaktadır.  
  
 Daha az karmaşık `IQueryable` sağlayıcısı tek bir Web hizmeti yöntem ile arabirim. Bu türden bir sağlayıcı, işlediği sorgularda belirli bilgiler beklediği için çok özeldir. Muhtemelen tek bir sonuç türü ortaya çıkaran kapalı bir tür sistemi vardır. Örneğin kullanarak sorgunun yürütülmesi, çoğu yerel olarak oluşur <xref:System.Linq.Enumerable> standart sorgu işleçleri uygulamaları. Daha az karmaşık olan bir sağlayıcı, sorguyu temsil eden ifade ağacında yalnızca bir yöntem çağrısı ifadesi inceleyebilir ve kalan sorgu mantığının başka bir yerde işlenmesine izin verebilir.  
  
 Bir `IQueryable` Orta karmaşıklık sağlayıcısı kısmen açıklayıcı sorgu dili olan bir veri kaynağına hedef. Bir Web hizmetini hedefliyorsa, Web hizmetinin birden fazla yöntemiyle arabirim oluşturabilir ve sorgunun sorduğu soruya göre bir çağrı yöntemi seçebilir. Orta düzeyde karmaşıklığa sahip bir sağlayıcının basit bir sağlayıcıya göre daha zengin bir tür sistemi vardır, ancak yine de sabit bir tür sistemidir. Örneğin, sağlayıcı ters çevrilebilen bire çok ilişkilerine sahip türleri kullanabilir, ancak kullanıcı tanımlı türler için eşleştirme teknolojisi sağlamaz.  
  
 Karmaşık bir `IQueryable` sağlayıcısı gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sağlayıcısı Çevir tam [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] SQL gibi bir açıklayıcı sorgu dili sorgular. Karmaşık bir sağlayıcı, sorguda çok çeşitli soruları işleyebileceği için daha az karmaşık olan bir sağlayıcıya göre daha geneldir. Ayrıca, açık bir tür sistemine de sahiptir ve bu nedenle kullanıcı tanımlı türleri eşleştirmek için kapsamlı bir altyapı içermelidir. Karmaşık bir sağlayıcının geliştirilmesi için önemli ölçüde çaba gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.IQueryable%601>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 <xref:System.Linq.Enumerable>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ to nesneler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
