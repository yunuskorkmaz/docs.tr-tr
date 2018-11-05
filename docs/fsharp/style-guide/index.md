---
title: 'F # Stil Kılavuzu'
description: 'İyi F # kodu beş sürecin prensiplerini öğrenin.'
ms.date: 05/14/2018
ms.openlocfilehash: 1d0f4e2a946f0cc91f376ba624f847549a830bc7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "34235911"
---
# <a name="f-style-guide"></a>F # Stil Kılavuzu

Aşağıdaki makaleler, biçimlendirme F # kodu tasarlamayla rehberlik için dil özelliklerinin ve nasıl kullanılması için yönergeleri açıklar.

Temel şeklide bu kılavuzun farklı grubunun kullanımını F # büyük kod tabanlarında. Bu kılavuz, genel olarak F # bu kadar başarılı kullanımı için müşteri adayları ve programlar için gereksinimleri zamanla değiştiğinde frustrations en aza indirir.

## <a name="five-principles-of-good-f-code"></a>Beş iyi F # kodu ilkeleri

Özellikle zamanla değişeceğini sistemlerinde F # kodu yazmak istediğiniz zaman aşağıdaki ilkeleri akılda tutulması. Daha fazla makale kılavuzunda her parça bu beş noktalarından kaynaklanır.

1. **Birleştiren ve ifadesel iyi F # kodu.**

    F # daha az kod satırı eylemleri express ve genel işlevler yeniden olanak tanıyan birçok özelliğe sahiptir. F # çekirdek kitaplığının ayrıca birçok yararlı türleri ve verinin genel koleksiyonlar ile çalışma için işlevleri içerir. Bir çözüme daha az kod satırı olası bir sorunu ifade edebilirsiniz, genel bir kural, diğer geliştiriciler (veya gelecekte, kendi kendine) appreciative olacaktır. FSharp.core'da gibi bir kitaplık kullanmak da önemle tavsiye edilir [geniş .NET kitaplıkları](https://docs.microsoft.com/dotnet/api/) , F # çalışan veya bir üçüncü taraf paketi [NuGet](https://www.nuget.org/) ölçeklenebilmesi kolay bir görev gerektiğinde.

2. **İyi F # kodu birlikte çalışabilir.**

    Birlikte çalışabilirlik, farklı dillerde kod kullanma dahil olmak üzere birden fazla form alabilir. Diğer çağıranlar birlikte çalışmanız kodunuzun doğru hale getirmek için kritik parçaları sınırlarıdır. F # yazarken, her zaman dahil olmak üzere C# gibi başka bir dilden bunu, yazmakta olduğunuz koda çağıran nasıl diğer kod hakkında düşünmek. [F # bileşeni tasarım yönergeleri](component-design-guidelines.md) birlikte çalışabilirlik ayrıntılı açıklanmaktadır.

3. **İyi F # kodu yapar nesne programlamasını kullanan, nesne olmayan yönü**

    F #, .NET nesneleri ile programlama için tam destek sahip dahil olmak üzere [sınıfları](../language-reference/classes.md), [arabirimleri](../language-reference/interfaces.md), [erişim değiştiricilerine](../language-reference/access-control.md), [soyut sınıflar](../language-reference/abstract-classes.md)ve benzeri. Bağlama duyarlı işlevleri gibi daha karmaşık işlev kodu için nesneleri işlevler olamaz yollarla bağlamsal bilgileri kolayca yalıtabilirsiniz. Gibi özellikleri [isteğe bağlı parametreler](../language-reference/members/methods.md#optional-arguments) ve dikkatli kullanımını [aşırı yükleme](../language-reference/members/methods.md#overloaded-methods) tüketim bu işlevsellik için çağıranlar kolaylaştırabilir.

4. **Mutasyon iyi sokmadan iyi F # kodu gerçekleştirir.**

    Yüksek performanslı kod yazmak için Mutasyon kullanmanız gerekir sır değildir. Bu, nasıl, tüm iş bilgisayarlarına olur. Bu tür kod genellikle hata yapmaya açık ve doğru hale getirmek zor. Arayanlara Mutasyon gösterme kaçının. Bunun yerine, [Mutasyon tabanlı bir uygulama gizler işlevsel bir arabirimi oluşturma](conventions.md#performance) performans olduğunda kritik.

5. **İyi F # kodu oluşturulabildiğinden**

    Araçlar her içinde çalışma büyük kod tabanlarında ve F # dil araçları ile daha etkili bir şekilde kullanılabilir olacak şekilde, F # kodu yazabilirsiniz. Örneğin, böylece bir hata ayıklayıcı ile Ara değerleri denetlenecek programlama, noktası serbest stil ile kaçmayın emin olmak. Başka bir örnek kullanarak [XML belgeleri yorumları](../language-reference/xml-documentation.md) düzenleyicilerde araç ipuçları bu yorumlar çağıran sitede görüntüleyebilir, yapıları açıklayan. Her zaman nasıl kodunuzu okunabilir, gittiğinizde, hata ayıklama ve diğer programcılar kendi araçlarıyla tarafından yönetilen düşünün.

## <a name="next-steps"></a>Sonraki adımlar

[Biçimlendirme yönergelerine F # kodu](formatting.md) okumak daha kolaydır, böylece kod biçimlendirme konusunda rehberlik sağlar.

[F # kodlama kuralları](conventions.md) F # büyük F # bu kadar uzun süreli bakım yardımcı olacak deyimleri programlama kod tabanlarında rehberlik sağlar.

[F # bileşeni tasarım yönergeleri](component-design-guidelines.md) kitaplıkları gibi F # bileşenleri, yazma için yönergeler sağlar.
