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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8645f77c8d03a475fe0fcc49f3e6d5e28829f9e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026139"
---
# <a name="localizability-review"></a>Yerelleştirilebilirlik incelemesi

Yerelleştirilebilirlik gözden geçirmesi dünya çapında kullanılmaya hazır uygulama geliştirmeyi Ara bir adımdır. Genelleştirilmiş bir uygulamayı yerelleştirme için hazırdır ve herhangi bir kod veya özel işlem gerektiren kullanıcı arabirimi yönleri tanımlar doğrular. Bu adım ayrıca yerelleştirme işlemi herhangi bir işlev hatasıyla uygulamanıza neden olmaz emin olun yardımcı olur. Yerelleştirilebilirlik gözden geçirmesi tarafından oluşturulan tüm sorunları ele, uygulamanızın yerelleştirme için hazırdır. Yerelleştirilebilirlik gözden geçirmesi kapsamlı ise, yerelleştirme işlemi sırasında herhangi bir kaynak kodu değiştirmek olmamalıdır.

Yerelleştirilebilirlik gözden geçirmesi aşağıdaki üç denetimleri oluşur:

- [Genelleştirme önerileri uygulanır?](#global)

- [Kültüre duyarlı özellikleri doğru bir şekilde ele alınır?](#culture)

- [Uygulamanızın uluslararası verilerle sınanmıştır?](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a>Genelleştirme önerileri uygulayın

Tasarlanmış ve geliştirilmiş yerelleştirme aklınızda uygulamanızla ve öneriler, izlediyseniz ele [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) makalenin yerelleştirilebilirlik gözden geçirmesi kalite güvencesi geçişi büyük ölçüde olacaktır . Aksi takdirde, bu aşamada gözden geçirmeli ve uygulamak için öneriler [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) ve yerelleştirme engelleyen kaynak kodundaki hataları düzeltin.

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a>Kültüre duyarlı özellikleri işleme

.NET kültür tarafından yaygın olarak farklı alanlar, çeşitli programlama desteği sağlamaz. Çoğu durumda, aşağıdaki gibi özellik alanları işlemek için özel kod yazmanız gerekir:

- Adresler

- Telefon numaraları

- Kağıt boyutları

- Uzunlukları, ağırlıkları, alan, birim ve sıcaklıklar için kullanılan ölçü birimleri

   .NET ölçü arasında dönüştürmek için yerleşik destek sunmaz olsa da, kullanabileceğiniz <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliği aşağıdaki örnekte gösterildiği gibi belirli bir ülke veya bölge Ölçüm sistemi kullanıp kullanmadığını belirlemek için.

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a>Uygulamanızı test edin

Uygulamanızı yerelleştirmek önce uluslararası işletim sistemi sürümlerinde uluslararası veriler kullanarak test etmeniz gerekir. Çoğu kullanıcı arabiriminin bu noktada yerelleştirilmez olsa da, aşağıdaki gibi sorunları algılamak mümkün olacaktır:

- Doğru işletim sistemi sürümleri arasında serisini değil, serileştirilmiş veriler.

- Geçerli kültürün kuralları yansıtmaz sayısal veriler. Örneğin, sayılar, yanlış Grup ayırıcıları, ondalık ayırıcı veya para birimi simgeleri görüntülenebilir.

- Geçerli kültürün kuralları yansıtmaz tarih ve saat verileri. Örneğin, ayı ve günü temsil eden sayı yanlış sırada görünebilir, tarih ayırıcı yanlış olabilir veya saat dilimi bilgilerini yanlış olabilir.

- Bir varsayılan kültür, uygulamanız için belirlediğiniz değil çünkü bulunamayan kaynaklar.

- Olağan dışı bir sırada belirli bir kültür için görüntülenen dize.

- Dize karşılaştırmaları veya beklenmeyen sonuçlar döndüren eşitlik karşılaştırmaları.

Sizin Uygulamanızı geliştirirken Genelleştirme önerileri takip, kültüre duyarlı özellikleri doğru işlendiğini ve ve test sırasında çıkan Yerelleştirme sorunları ele, sonraki adıma geçebilirsiniz [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md)
- [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
