---
title: "Veri kaynağı için LINQ Querying2 etkinleştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a6ec979c4c7ed36a9b9f56b04de762fe4ec7fec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]uygulayan sağlayıcılar <xref:System.Linq.IQueryable%601> kendi karmaşıklık yaygın olarak değişebilir. Bu bölümde, farklı karmaşıklık düzeyleri açıklanmaktadır.  
  
 Daha az karmaşık `IQueryable` sağlayıcısı tek bir Web hizmeti yöntem ile arabirim. Bu türden bir sağlayıcı, işlediği sorgularda belirli bilgiler beklediği için çok özeldir. Muhtemelen tek bir sonuç türü ortaya çıkaran kapalı bir tür sistemi vardır. Örneğin kullanarak sorgunun yürütülmesi, çoğu yerel olarak oluşur <xref:System.Linq.Enumerable> standart sorgu işleçleri uygulamaları. Daha az karmaşık olan bir sağlayıcı, sorguyu temsil eden ifade ağacında yalnızca bir yöntem çağrısı ifadesi inceleyebilir ve kalan sorgu mantığının başka bir yerde işlenmesine izin verebilir.  
  
 Bir `IQueryable` Orta karmaşıklık sağlayıcısı kısmen açıklayıcı sorgu dili olan bir veri kaynağına hedef. Bir Web hizmetini hedefliyorsa, Web hizmetinin birden fazla yöntemiyle arabirim oluşturabilir ve sorgunun sorduğu soruya göre bir çağrı yöntemi seçebilir. Orta düzeyde karmaşıklığa sahip bir sağlayıcının basit bir sağlayıcıya göre daha zengin bir tür sistemi vardır, ancak yine de sabit bir tür sistemidir. Örneğin, sağlayıcı ters çevrilebilen bire çok ilişkilerine sahip türleri kullanabilir, ancak kullanıcı tanımlı türler için eşleştirme teknolojisi sağlamaz.  
  
 Karmaşık bir `IQueryable` sağlayıcısı gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sağlayıcısı Çevir tam [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] SQL gibi bir açıklayıcı sorgu dili sorgular. Karmaşık bir sağlayıcı, sorguda çok çeşitli soruları işleyebileceği için daha az karmaşık olan bir sağlayıcıya göre daha geneldir. Ayrıca, açık bir tür sistemine de sahiptir ve bu nedenle kullanıcı tanımlı türleri eşleştirmek için kapsamlı bir altyapı içermelidir. Karmaşık bir sağlayıcının geliştirilmesi için önemli ölçüde çaba gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.IQueryable%601>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 <xref:System.Linq.Enumerable>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ to nesneler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
