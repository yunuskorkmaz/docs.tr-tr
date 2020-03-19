---
title: F# stil kılavuzu
description: İyi F# kodunun beş ilkesini öğrenin.
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400269"
---
# <a name="f-style-guide"></a>F# stil kılavuzu

Aşağıdaki makaleler, Dilin özellikleri ve bunların nasıl kullanılması gerektiği için F# kodunu ve topikal kılavuzu biçimlendirme yönergelerini açıklar.

Bu kılavuz, farklı programcılar grubuyla büyük kod tabanlarında F# kullanımına göre formüle edilmiştir. Bu kılavuz genellikle F# kullanımının başarılı bir şekilde kullanılmasına yol açar ve programların gereksinimleri zaman içinde değiştiğinde hayal kırıklıklarını en aza indirir.

## <a name="five-principles-of-good-f-code"></a>İyi F# kodunun beş prensibi

F# kodunu her yazdığınızda, özellikle zaman içinde değişecek sistemlerde aşağıdaki ilkeleri aklınızda bulundurun. Daha sonraki makalelerde rehberlik her parçası bu beş noktadan kaynaklanmaktadır.

1. **İyi F# kodu kısa, anlamlı ve uyumludur**

    F# eylemleri daha az kod satırında ifade etmenize ve genel işlevselliği yeniden kullanmanıza olanak tanıyan birçok özelliğe sahiptir. F# çekirdek kitaplığı, ortak veri koleksiyonlarıyla çalışmak için birçok yararlı tür ve işlev de içerir. Kendi işlevlerinizin ve F# çekirdek kitaplığındakilerin (veya diğer kitaplıkların) bileşimi, rutin deyimsel F# programlamasının bir parçasıdır. Genel bir kural olarak, bir sorunun çözümünün daha az kod satırında ifade edebilirseniz, diğer geliştiriciler (veya gelecekteki benliğiniz) minnettar olacaktır. Ayrıca, FSharp.Core gibi bir kitaplığı, F# üzerinde çalıştığı [geniş .NET kitaplıklarını](../../../api/index.md) veya önemsiz bir görevi yapmanız gerektiğinde [NuGet'de](https://www.nuget.org/) üçüncü taraf paketi kullanmanız önerilir.

2. **İyi F# kodu birlikte çalışabilir**

    İşlemler, farklı dillerde kod tüketmek de dahil olmak üzere birden çok form alabilir. Diğer arayanların birlikte çalıştığı kodunuzun sınırları, arayanlar da F#'da olsa bile, doğru yapmak için kritik parçalardır. F# yazarken, c# gibi başka bir dilden bunu yapmak da dahil olmak üzere, her zaman diğer kodun yazdığınız koda nasıl çağrıyapacağını düşünmelisiniz. [F# Bileşeni Tasarım Yönergeleri](component-design-guidelines.md) birlikte çalışabilirliği ayrıntılı olarak açıklar.

3. **İyi F# kodu nesne yönlendirmesini değil, nesne programlamayı kullanır**

    F# [sınıflar,](../language-reference/classes.md) [arabirimler,](../language-reference/interfaces.md) [erişim değiştiriciler,](../language-reference/access-control.md) [soyut sınıflar](../language-reference/abstract-classes.md)ve benzeri dahil olmak üzere .NET nesneleri ile programlama için tam destek vardır. Bağlam bilgisine sahip olması gereken işlevler gibi daha karmaşık işlevsel kodlar için nesneler bağlamsal bilgileri işlevlerin yapamadığı şekillerde kolayca saklayabilir. [İsteğe bağlı parametreler](../language-reference/members/methods.md#optional-arguments) ve [aşırı yüklemenin](../language-reference/members/methods.md#overloaded-methods) dikkatli kullanımı gibi özellikler, arayanlar için bu işlevselliğin tüketimini kolaylaştırabilir.

4. **İyi F# kodu mutasyonu ortaya çıkarmadan iyi bir performans sergiliyor**

    Yüksek performanslı kod yazmak için mutasyon uyguluyorsun. Ne de olsa bilgisayarlar böyle çalışır. Bu tür kod genellikle hata eğilimli ve doğru almak zordur. Mutasyonu arayanlara maruz bırakmaktan kaçının. Bunun yerine, performans kritik olduğunda [mutasyon tabanlı bir uygulamayı gizleyen işlevsel bir arabirim oluşturun.](conventions.md#performance)

5. **İyi F# kodu araç olabilir**

    Araçlar büyük codebases çalışmak için paha biçilmez ve F # dil aracı ile daha etkili bir şekilde kullanılabilir şekilde F # kodu yazabilirsiniz. Bir örnek, ara değerlerin hata ayıklama yla denetlenebilmeleri için, anlamsız bir programlama stiliyle aşırıya kaldığınızdan emin olmaktır. Başka bir örnek, düzenleyicilerdeki araç ipuçlarının çağrı sitesinde bu yorumları görüntüleyebildiği yapıları açıklayan [XML dokümantasyon açıklamaları](../language-reference/xml-documentation.md) kullanmaktır. Her zaman kodunuzu nasıl okunacağını, gezineceğini, debugged ve kendi araçları ile diğer programcılar tarafından manipüle düşünüyorum.

## <a name="next-steps"></a>Sonraki adımlar

[F# kod biçimlendirme yönergeleri,](formatting.md) okunabilmek için kodun nasıl biçimlendirilene kadar biçimlendirilene ilişkin kılavuz sağlar.

[F# kodlama kuralları,](conventions.md) daha büyük F# kod tabanlarının uzun süreli bakımına yardımcı olacak F# programlama deyimleri için kılavuz sağlar.

[F# bileşeni tasarım yönergeleri,](component-design-guidelines.md) kitaplıklar gibi F# bileşenlerinin yazilmesi için kılavuz sağlar.
