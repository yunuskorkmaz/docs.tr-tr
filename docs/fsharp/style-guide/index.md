---
title: F#Stil Kılavuzu
description: İyi beş sürecin prensiplerini öğrenin F# kod.
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61901855"
---
# <a name="f-style-guide"></a>F#Stil Kılavuzu

Aşağıdaki makaleler biçimlendirme yönergeleri açıklar F# kod ve güncel yönergeler için dil özelliklerinin ve nasıl kullanılır.

Kullanıma bağlı şeklide bu kılavuzun F# içinde büyük ile farklı grubunun çıkabilirsiniz. Bu kılavuz, genellikle başarılı kullanımı için müşteri adayları F# ve program için gereksinimleri zamanla değiştiğinde frustrations en aza indirir.

## <a name="five-principles-of-good-f-code"></a>Beş iyi prensipleri F# kod

Aşağıdaki ilkeler yazmanıza dilediğiniz zaman göz önünde bulundurun F# özellikle zamanla değişeceğini sistemlerinde kod. Daha fazla makale kılavuzunda her parça bu beş noktalarından kaynaklanır.

1. **İyi F# kodu birleştiren, ifadesel ve birleştirilebilir.**

    F#daha az kod satırı eylemleri express ve genel işlevler yeniden olanak tanıyan birçok özelliğe sahiptir. F# Çekirdek kitaplığı de içeren pek çok yararlı türleri ve işlevleri için ortak veri koleksiyonlar ile çalışma. Kendi işlevleri ve bu, oluşumunu F# çekirdek kitaplığı (veya diğer kitaplıkları) yordamı deyimsel bir parçası olan F# programlama. Bir çözüme daha az kod satırı olası bir sorunu ifade edebilirsiniz, genel bir kural, diğer geliştiriciler (veya gelecekte, kendi kendine) appreciative olacaktır. FSharp.core'da gibi bir kitaplık kullanmak da önemle tavsiye edilir [geniş .NET kitaplıkları](../../../api/index.md) , F# üzerinde çalıştığı veya bir üçüncü taraf paketi [NuGet](https://www.nuget.org/) ölçeklenebilmesi kolay bir görev gerektiğinde.

2. **İyi F# kodu birlikte çalışabilir.**

    Birlikte çalışabilirlik, farklı dillerde kod kullanma dahil olmak üzere birden fazla form alabilir. Çağıranlar de olsalar bile sağ almak için kritik parçaları sınırlarıdır kodunuzun diğer çağıranlar birlikte çalışmanız F#. Yazarken F#, size her zaman hakkında nasıl başka bir kod yazdığınız, bunlar gibi başka bir dilden yaparsanız dahil olmak üzere kod içine çağıracak düşünmek C#. [ F# Bileşen tasarım yönergeleri](component-design-guidelines.md) birlikte çalışabilirlik ayrıntılı açıklanmaktadır.

3. **İyi F# nesne programlamasını kullanan, nesne olmayan kod yapar yönü**

    F#. NET'te, nesneleri ile programlama için tam destek sahip dahil olmak üzere [sınıfları](../language-reference/classes.md), [arabirimleri](../language-reference/interfaces.md), [erişim değiştiricilerine](../language-reference/access-control.md), [soyut sınıflar](../language-reference/abstract-classes.md)ve benzeri. Bağlama duyarlı işlevleri gibi daha karmaşık işlev kodu için nesneleri işlevler olamaz yollarla bağlamsal bilgileri kolayca yalıtabilirsiniz. Gibi özellikleri [isteğe bağlı parametreler](../language-reference/members/methods.md#optional-arguments) ve dikkatli kullanımını [aşırı yükleme](../language-reference/members/methods.md#overloaded-methods) tüketim bu işlevsellik için çağıranlar kolaylaştırabilir.

4. **İyi F# kod da Mutasyon sokmadan gerçekleştirir**

    Yüksek performanslı kod yazmak için Mutasyon kullanmanız gerekir sır değildir. Bu, nasıl, tüm iş bilgisayarlarına olur. Bu tür kod genellikle hata yapmaya açık ve doğru hale getirmek zor. Arayanlara Mutasyon gösterme kaçının. Bunun yerine, [Mutasyon tabanlı bir uygulama gizler işlevsel bir arabirimi oluşturma](conventions.md#performance) performans olduğunda kritik.

5. **İyi F# oluşturulabildiğinden kodu.**

    İçinde çalışma büyük kod tabanlarında ve yazabileceğiniz araçları her F# ile daha etkili bir şekilde kullanılabilir olacağı şekilde kod F# dil araçları. Örneğin, böylece bir hata ayıklayıcı ile Ara değerleri denetlenecek programlama, noktası serbest stil ile kaçmayın emin olmak. Başka bir örnek kullanarak [XML belgeleri yorumları](../language-reference/xml-documentation.md) düzenleyicilerde araç ipuçları bu yorumlar çağıran sitede görüntüleyebilir, yapıları açıklayan. Her zaman nasıl kodunuzu okunabilir, gittiğinizde, hata ayıklama ve diğer programcılar kendi araçlarıyla tarafından yönetilen düşünün.

## <a name="next-steps"></a>Sonraki adımlar

[ F# Kod biçimlendirme yönergeleri](formatting.md) okumak daha kolaydır, böylece kod biçimlendirme konusunda rehberlik sağlar.

[ F# Kodlama kuralları](conventions.md) için rehberlik F# büyük uzun süreli bakım yardımcı olacak deyimleri programlama F# çıkabilirsiniz.

[ F# Bileşen tasarım yönergeleri](component-design-guidelines.md) yazmak için rehberlik F# kitaplıkları gibi bileşenleri.
