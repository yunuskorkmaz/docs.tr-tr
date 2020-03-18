---
title: Yerelleştirilebilirlik İncelemesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: b286bdd2c5d7b03a0a2b5f94478e252da6cd0ae2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120856"
---
# <a name="localizability-review"></a>Yerelleştirilebilirlik incelemesi

Yerelleştirilebilirlik incelemesi, dünyaya hazır bir uygulamanın geliştirilmesinde ara adımdır. Küreselleştirilmiş bir uygulamanın yerelleştirme için hazır olduğunu doğrular ve kullanıcı arabiriminin özel işleme gerektiren herhangi bir kodu veya herhangi bir yönünü tanımlar. Bu adım, yerelleştirme işleminin uygulamanıza işlevsel hatalar getirmemesini de sağlamaya yardımcı olur. Yerelleştirilebilirlik incelemesi tarafından ortaya atılan tüm sorunlar ele alındığunda, başvurunuz yerelleştirme için hazırdır. Yerelleştirilebilirlik incelemesi kapsamlıysa, yerelleştirme işlemi sırasında herhangi bir kaynak kodu değiştirmeniz gerekmez.

Yerelleştirilebilirlik incelemesi aşağıdaki üç denetimden oluşur:

- [Küreselleşme önerileri uygulanıyor mu?](#global)

- [Kültüre duyarlı özellikler doğru işlenir mi?](#culture)

- [Başvurunuzu uluslararası verilerle test ettiniz mi?](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a>Küreselleşme önerilerini uygulama

Uygulamanızı yerelleştirme yi göz önünde bulundurarak tasarladıysanız ve geliştirdiyseniz ve [Küreselleşme](../../../docs/standard/globalization-localization/globalization.md) makalesinde tartışılan tavsiyelere uyduysanız, yerelleştirilebilirlik incelemesi büyük ölçüde bir kalite güvencesi geçişi olacaktır. Aksi takdirde, bu [aşamada, küreselleşme](../../../docs/standard/globalization-localization/globalization.md) için önerileri gözden geçirmeli ve uygulamalı ve yerelleştirmeyi engelleyen kaynak kodundaki hataları düzeltmelisiniz.

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a>Kültüre duyarlı özellikleri işleme

.NET, kültüre göre büyük farklılıklar gösteren alanlarda programlı destek sağlamaz. Çoğu durumda, aşağıdaki gibi özellik alanlarını işlemek için özel kod yazmanız gerekir:

- Adresler

- Telefon numaraları

- Kağıt boyutları

- Uzunluklar, ağırlıklar, alan, hacim ve sıcaklıklar için kullanılan ölçü birimleri

   .NET, ölçü birimleri arasında dönüştürme için yerleşik destek sunmasa da, aşağıdaki örnekte gösterildiği gibi, belirli bir ülkenin veya bölgenin metrik sistemi kullanıp kullanmadığını belirlemek için <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliği kullanabilirsiniz.

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a>Başvurunuzu test edin

Uygulamanızı yerelleştirmeden önce, işletim sisteminin uluslararası sürümlerinde uluslararası verileri kullanarak uygulamayı test etmelisiniz. Kullanıcı arabiriminin çoğu bu noktada yerelleştirilmese de, aşağıdaki gibi sorunları algılayabilirsiniz:

- İşletim sistemi sürümlerinde doğru şekilde deserialize olmayan serileştirilmiş veriler.

- Geçerli kültürün kurallarını yansıtmayan sayısal veriler. Örneğin, sayılar yanlış grup ayırıcıları, ondalık ayırıcılar veya para birimi sembolleri ile görüntülenebilir.

- Geçerli kültürün kurallarını yansıtmayan tarih ve saat verileri. Örneğin, ay ve günü temsil eden sayılar yanlış sırada görünebilir, tarih ayırıcıları yanlış olabilir veya saat dilimi bilgileri yanlış olabilir.

- Uygulamanız için varsayılan bir kültür tanımlamadığınız için bulunamayan kaynaklar.

- Belirli bir kültür için alışılmadık bir sırada görüntülenen dizeleri.

- Beklenmeyen sonuçlar döndüren eşitlik için dize karşılaştırmaları veya karşılaştırmalar.

Uygulamanızı geliştirirken küreselleşme önerilerini izlediyseniz, kültüre duyarlı özellikleri doğru şekilde ele aldıysanız ve test sırasında ortaya çıkan yerelleştirme sorunlarını tespit edip ele aldıysanız, bir sonraki adımolan [Yerelleştirme'ye](../../../docs/standard/globalization-localization/localization.md)geçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md)
- [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)
- [Masaüstü Uygulamalarında Kaynaklar](../../../docs/framework/resources/index.md)
