---
title: "Yerelleştirilebilirlik Gözden Geçirmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a>Yerelleştirilebilirlik Gözden Geçirmesi
Yerelleştirilebilirlik gözden geçirme, dünya çapında kullanılmaya hazır uygulama geliştirmede Ara bir adımdır. Globalized uygulama yerelleştirme için hazır ve herhangi bir kod veya özel işlem gerektiren tüm yönlerini kullanıcı arabirimini tanımlar doğrular. Bu adım ayrıca yerelleştirme işlemi işlev bozuklukları uygulamanıza tanıtılacaktır değil, sağlamaya yardımcı olur. Yerelleştirilebilirlik gözden geçirmesi tarafından gerçekleştirilen tüm sorunlar ele uygulamanızı yerelleştirme için hazır olur. Yerelleştirilebilirlik gözden geçirmesi kapsamlı ise, herhangi bir kaynak kod yerelleştirme işlemi sırasında değiştirmek olmamalıdır.  
  
 Yerelleştirilebilirlik gözden geçirmesi aşağıdaki üç çekler oluşur:  
  
-   [Genelleştirme önerileri uygulanır?](#global)  
  
-   [Kültüre duyarlı özellikleri doğru şekilde işlenir?](#culture)  
  
-   [Uygulamanızı uluslararası verilerle sınanmıştır?](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>Uygulama genelleştirme önerileri  
 Tasarlanmış ve yerelleştirme aklınızda uygulamanızla geliştirilmiştir ve öneriler, izlediyseniz ele [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) makalenin yerelleştirilebilirlik gözden geçirmesi büyük ölçüde kalite güvence geçişi olacaktır . Aksi takdirde, bu aşamada gözden geçirmeli ve uygulamak için öneriler [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)ve kaynak kodunda yerelleştirme önlemek hataları düzeltin.  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>Kültüre duyarlı özellikleri işleme  
 .NET Framework tarafından kültür büyük ölçüde farklılık alanları çeşitli programlama desteği sağlamaz. Çoğu durumda, aşağıdaki gibi özellik alanları işlemek için özel kod yazmanıza vardır:  
  
-   Adresleri.  
  
-   Telefon numaraları.  
  
-   Kağıt boyutları.  
  
-   Ölçü birimi uzunlukları, ağırlıkları, alan, birim ve etme için kullanılır. .NET Framework ölçü arasında dönüştürme için yerleşik destek sağlamaz, ancak kullanabilirsiniz <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliği aşağıdaki örnekte gösterildiği gibi belirli bir ülke veya bölge Metrik sistem kullanıp kullanmadığını belirleyin.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>Uygulamanızı sınama  
 Uygulamanızı yerelleştirme önce uluslararası işletim sistemi sürümlerinde uluslararası verileri kullanarak test etmeniz gerekir. Çoğu kullanıcı arabirimi, bu noktada yerelleştirilmiş olabilir değil de, aşağıdaki gibi sorunlar algılayabilir olacaktır:  
  
-   Doğru işletim sistemi sürümleri arasında serisini değil serileştirilmiş veriler.  
  
-   Geçerli kültür kuralları yansıtmaz sayısal veriler. Örneğin, numaraları yanlış Grup ayırıcılar, ondalık ayırıcı veya para birimi simgeleri görüntülenebilir.  
  
-   Geçerli kültür kuralları yansıtmaz tarih ve saat verileri. Örneğin, ayı ve günü temsil eden sayı yanlış sırayla görünebilir, tarih ayırıcıları yanlış olabilir veya saat dilimi bilgileri hatalı olabilir.  
  
-   Varsayılan kültürü uygulamanız için tanımladığınız değil çünkü bulunamayan kaynaklar.  
  
-   Olağan dışı bir sırada belirli kültür için görüntülenen dizeleri.  
  
-   Karşılaştırmaları veya beklenmeyen sonuçlar döndürebilir karşılaştırmaları eşitlik için dize.  
  
 Artık Uygulamanızı geliştirirken Genelleştirme önerileri ve ardından, kültüre duyarlı özellikleri, doğru ele ve tanımlanan ve test sırasında çıkan yerelleştirme sorunlar ele, sonraki adıma geçebilirsiniz [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genelleştirme ve yerelleştirme](../../../docs/standard/globalization-localization/index.md)  
 [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md)  
 [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)  
 [Masaüstü uygulamalarındaki kaynaklar](../../../docs/framework/resources/index.md)
