---
title: 'F # Stil Kılavuzu'
description: 'İyi F # kodu beş ilkeleri hakkında bilgi edinin.'
ms.date: 05/14/2018
ms.openlocfilehash: 317fc2c101449b0500a54dd9fea3d426757af5cd
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="f-style-guide"></a>F # Stil Kılavuzu

Aşağıdaki makaleler için biçimlendirme F # kodu ve dil özellikleri için güncel kılavuzunu ve nasıl kullanıldıkları yönergeleri açıklar.

Temel şeklide bu kılavuzun farklı programcıları grubuyla kullanımını F # büyük olarak kullanılabilecek kod temeli. Bu kılavuz, genellikle başarılı kullanımını F # için müşteri adayları ve program için gereksinimleri zamanla değiştirdiğinizde frustrations en aza indirir.

## <a name="five-principles-of-good-f-code"></a>Beş ilkeleri iyi F # kodu

Aşağıdaki ilkeleri özellikle zaman içinde değişir sistemlerinde F # kod yazmayı dilediğiniz zaman göz önünde bulundurmalıdır. Daha fazla makaleleri kılavuzunda her parçasının bu beş noktalarından kaynaklandığını.

1. **Kısa ve açıklayıcı iyi F # kodu.**

    F # daha az satır kod Eylemler hızlı ve genel işlevler yeniden olanak sağlayan birçok özelliğe sahiptir. F # core kitaplık pek çok yararlı türler ve İşlevler veri ortak koleksiyonları ile çalışmak için de içerir. Daha az satır kod, bir sorun için çözüm express genel kural olarak, diğer geliştiricilere (veya gelecekteki self) appreciative tutulur. Ayrıca yüksek oranda FSharp.Core gibi bir kitaplığı kullanmanız önerilir [büyük .NET kitaplıklarına](https://docs.microsoft.com/dotnet/api/) F #, üzerinde çalışan veya bir üçüncü taraf paket [NuGet](https://www.nuget.org/) ölçeklendirebilmek kolay değildir bir görev gerektiğinde.

2. **İyi F # kodu birlikte çalışabilir.**

    Birlikte çalışabilirlik kodu farklı dillerde kullanma dahil olmak üzere birden fazla form alabilir. Diğer arayanlar birlikte çalışmanız kodunuzun doğru almak için kritik parça sınırlarıdır. F # yazarken, her zaman nasıl diğer kod hakkında bunu C# gibi başka bir dilden içermiyorlarsa dahil olmak üzere, yazıyorsanız koda çağıracak düşünüyorum. [F # bileşen tasarım yönergeleri](component-design-guidelines.md) birlikte çalışabilirlik ayrıntılı açıklamaktadır.

3. **İyi F # kod yapar, nesne programlama kullanın, olmayan nesne yönü**

    F # .NET ile programlama nesneleri için tam destek sahip dahil olmak üzere [sınıfları](../language-reference/classes.md), [arabirimleri](../language-reference/interfaces.md), [erişim değiştiricileri](../language-reference/access-control.md), [soyut sınıflar](../language-reference/abstract-classes.md)ve benzeri. Bağlam algılayan işlevleri gibi daha karmaşık işlevsel kod için nesneleri işlevleri edilemez şekilde bağlamsal bilgileri kolayca yerleştirebilirsiniz. Gibi özellikleri [isteğe bağlı parametreler](../language-reference/members/methods.md#optional-arguments) ve [aşırı](../language-reference/members/methods.md#overloaded-methods) aynı zamanda bu işlevselliği tüketimi çağıranlar için yardımcı.

4. **İyi mutation sokmadan iyi F # kod gerçekleştirir**

    Yüksek performanslı kod yazmaya mutation kullanmanız gerekir hiçbir gizli olur. Bu bilgisayarlar, tüm nasıl olur. Bu tür genellikle sağ almak zor ve hataya yatkın kodudur. Arayanlara mutation gösterme kaçının. Bir işlev arabirimi mutation tabanlı bir uygulama arama.

5. **İyi F # kodu oluşturulabildiğinden.**

    Büyük çalışma olarak kullanılabilecek kod temeli için Araçlar çok değerli bir kaynak, F # kodu daha etkili bir şekilde F # Dili Araçları ile kullanılabilir gibi yazabilirsiniz. Bir örnek, böylece Ara değerleri ile bir hata ayıklayıcısı denetlenecek programlama, bir nokta serbest stiliyle overdo yok emin yapılmasıdır. Başka bir örnek kullanılarak [XML belgeleri yorumları](../language-reference/xml-documentation.md) düzenleyicileri ipuçlarında çağrısı sitede bu açıklamalar görüntüleyebilir, yapıları açıklayan. Her zaman nasıl kodunuzu okuyun, gittiğinizde, hata ayıklaması ve bunların araçları ile diğer programcıları tarafından yönetilebilir düşünün.

## <a name="next-steps"></a>Sonraki adımlar

[F # biçimlendirme yönergeleri](formatting.md) okumak kolayca böylece kodu biçimlendirmek konusunda rehberlik sağlar.

[F # kodlama kuralları](conventions.md) F # uzun vadeli büyük F # sürdürülmesine yardımcı olacak deyimleri programlama olarak kullanılabilecek kod temeli için rehberlik sağlar.

[F # bileşen tasarım yönergeleri](component-design-guidelines.md) F # gibi bileşenleri kitaplıkları yazma Kılavuzu kapsamlı bir kümesidir.