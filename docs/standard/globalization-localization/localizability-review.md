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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120856"
---
# <a name="localizability-review"></a>Yerelleştirilebilirlik incelemesi

Yerelleştirilebilirlik incelemesi, dünya çapında bir uygulama geliştirmenin bir ara adımıdır. Bir Genelleştirilmiş uygulamasının yerelleştirme için hazırlandığını doğrular ve herhangi bir kodu veya özel işleme gerektiren Kullanıcı arabiriminin herhangi bir yönlerini tanımlar. Bu adım Ayrıca yerelleştirme işleminin uygulamanıza işlevsel hatalar sunmaz. Yerelleştirilebilirlik incelemesi tarafından oluşturulan tüm sorunlar ele geçirilmemişse, uygulamanız yerelleştirme için hazırlayın. Yerelleştirilebilirlik incelemesi tam ise, yerelleştirme işlemi sırasında herhangi bir kaynak kodunu değiştirmeniz gerekmez.

Yerelleştirilebilirlik incelemesi, aşağıdaki üç denetimi içerir:

- [Genelleştirme önerileri uygulandı mi?](#global)

- [Kültüre duyarlı özellikler doğru şekilde işlensin mi?](#culture)

- [Uygulamanızı Uluslararası verilerle test etmeniz mi gerekiyor?](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a>Genelleştirme önerilerini Uygula

Uygulamanızı aklına göre tasarlanıp geliştirip geliştirdiyseniz ve [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) makalesinde açıklanan önerileri izlediyseniz, Yerelleştirilebilirlik incelemesi büyük ölçüde kalite güvencesi geçişine sahip olur. Aksi takdirde, bu aşamada [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) önerilerini gözden geçirmeniz ve uygulamanız ve kaynak koddaki yerelleştirmeyi önleyen hataları çözmeniz gerekir.

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a>Kültüre duyarlı özellikleri işleme

.NET, kültüre göre farklılık gösteren çeşitli alanlarda programlama desteği sağlamaz. Çoğu durumda, aşağıdaki gibi özellik alanlarının işlenmesi için özel kod yazmanız gerekir:

- Adresler

- Telefon numaraları

- Kağıt boyutları

- Uzunluk, ağırlık, alan, birim ve sıcaklıklar için kullanılan ölçü birimleri

   .NET, ölçü birimleri arasında dönüştürme için yerleşik destek sunmasa da, aşağıdaki örnekte gösterildiği gibi belirli bir ülkenin veya bölgenin ölçüm sistemini kullanıp kullanmadığını anlamak için <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliğini kullanabilirsiniz.

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a>Uygulamanızı test etme

Uygulamanızı yerelleştirebilmeniz için, işletim sisteminin Uluslararası sürümlerindeki Uluslararası verileri kullanarak test etmelisiniz. Bu noktada Kullanıcı arabiriminin büyük bir çoğunluğu yerelleştirilemez, ancak aşağıdaki gibi sorunları tespit edebilirsiniz:

- İşletim sistemi sürümlerinde doğru şekilde seri durumdan çıkarmayan serileştirilmiş veriler.

- Geçerli kültürün kurallarını yansıtmayan sayısal veriler. Örneğin, sayılar yanlış Grup ayırıcılar, Ondalık ayırıcılar veya para birimi sembolleri ile görüntülenebilir.

- Geçerli kültürün kurallarını yansıtmayan tarih ve saat verileri. Örneğin, ayı ve günü temsil eden sayılar yanlış sırada görünebilir, tarih ayırıcıları yanlış olabilir veya saat dilimi bilgisi yanlış olabilir.

- Uygulamanız için bir varsayılan kültür belirlemei olmadığınızdan, bulunamayan kaynaklar.

- Belirli kültür için olağan dışı bir düzende görüntülenen dizeler.

- Beklenmeyen sonuçlar döndüren eşitlik için dize karşılaştırmaları veya karşılaştırmalar.

Uygulamanızı geliştirirken Genelleştirme önerilerini izlediyseniz, kültüre duyarlı özellikleri doğru bir şekilde işlemişseniz ve test sırasında kullanılan yerelleştirme sorunlarını tanımladıysanız, bir sonraki adımla [devam edebilirsiniz. Yerelleştirme](../../../docs/standard/globalization-localization/localization.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md)
- [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
