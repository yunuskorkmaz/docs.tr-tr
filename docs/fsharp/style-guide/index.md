---
title: F# stil kılavuzu
description: 'İyi F # kodu için beş ilke öğrenin.'
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223656"
---
# <a name="f-style-guide"></a>F# stil kılavuzu

Aşağıdaki makalelerde, dilin özellikleri ve bunların nasıl kullanılması gerektiği hakkında F # kodu ve tasarlamayla ilgilenen Kılavuzu biçimlendirme yönergeleri açıklanır.

Bu kılavuz, farklı bir programcılar grubuyla büyük kod tabanlarında F # kullanımı temel alınarak formüle eklenmiştir. Bu kılavuz genellikle, F # ' ın başarılı bir şekilde kullanılmasına ve programlar için gereksinimler zaman içinde değiştiğinde yamaları en aza indirir.

## <a name="five-principles-of-good-f-code"></a>Beş adet iyi F # kodu ilkeleri

Aşağıdaki ilkeleri, özellikle zaman içinde değişen sistemlerde F # Code yazdığınızda her seferinde aklınızda bulundurun. Daha fazla makalelerdeki her bir kılavuzluk, bu beş noktadan itibaren yardımcı olur.

1. **İyi F # kodu kısa, ifade ve birleştirilebilir**

    F #, eylemleri daha az kod satırı halinde ifade etmeniz ve genel işlevselliği yeniden kullanmak için birçok özelliğe sahiptir. F # Çekirdek Kitaplığı ayrıca ortak veri koleksiyonlarıyla çalışmak için birçok yararlı tür ve işlev içerir. Kendi işlevlerinizin ve F # Çekirdek Kitaplığı 'nda (veya diğer kitaplıklarda) oluşturulması, yordam F # programlamanın bir parçasıdır. Genel bir kural olarak, bir çözümü daha az kod satırı içindeki bir soruna ifade edebilirsiniz, diğer geliştiriciler (veya gelecekteki self) de teşekkürler. Ayrıca, önemsiz olmayan bir görev yapmanız gerektiğinde, FSharp. Core, F # ' ın üzerinde çalıştığı büyük [.NET kitaplıkları](../../../api/index.md) veya [NuGet](https://www.nuget.org/) üzerinde bir üçüncü taraf paketi gibi bir kitaplık kullanmanız önerilir.

2. **İyi F # kodu birlikte çalışabilir**

    Birlikte çalışabilirlik, farklı dillerdeki kodu tüketme dahil olmak üzere birden çok form alabilir. Diğer çağıranların ile birlikte çalışan kodunuzun sınırları, arayanlar de F # içinde olsa bile, doğru bir şekilde daha fazla bilgi almak için önemli parçalardır. F # yazarken, diğer kodun yazdığınız koda nasıl çağrılacağını (örneğin, C# gibi başka bir dilde mi yapadıklarından) her zaman düşünmelisiniz. [F # bileşeni tasarım yönergeleri](component-design-guidelines.md) birlikte çalışabilirliği ayrıntılı olarak anlatmaktadır.

3. **İyi F # kodu nesne yönlendirmesini değil, nesne programlamayı kullanır**

    F #, [sınıflar](../language-reference/classes.md), [arabirimler](../language-reference/interfaces.md), [erişim değiştiricileri](../language-reference/access-control.md), [soyut sınıflar](../language-reference/abstract-classes.md)vb. dahil olmak üzere .NET içindeki nesnelerle programlama için tam desteğe sahiptir. Bağlam bilgisi olması gereken işlevler gibi daha karmaşık işlev kodu için nesneler, bağlama bilgilerini işlevlerin çalışmayacaklarını kolayca kapsülleyebilirsiniz. [İsteğe bağlı parametreler](../language-reference/members/methods.md#optional-arguments) ve dikkatli kullanım gibi [Özellikler, bu](../language-reference/members/methods.md#overloaded-methods) işlevselliği arayanlar için daha kolay hale getirir.

4. **İyi F # kodu, mutasyon olmadan iyi çalışır**

    Yüksek performanslı kod yazmanın gizli anahtarı yoktur, mutasyon kullanmanız gerekir. Bunlar, tüm bilgisayarlar için çalışır. Bu kod genellikle hataya açıktır ve hemen hemen zor olur. Çağıranlar için mutasyon 'yi açığa çıkarmaktan kaçının. Bunun yerine, performans önemli olduğunda [bir mutasyon tabanlı uygulamayı gizleyen işlevsel bir arabirim oluşturun](conventions.md#performance) .

5. **İyi F # kodu iyidir**

    Araçlar, büyük kod tabanlarında çalışmaya önem taşır ve f # kodu yazmak için F # dil araçları ile daha etkili bir şekilde kullanılabilir. Tek bir örnek, bir noktadan bağımsız programlama stiliyle bu işlemi gerçekleştirmemenizi ve bu sayede ara değerlerin bir hata ayıklayıcıyla incelenebilmesini sağlamak için bir örnektir. Diğer bir örnek yapıları açıklayan ve düzenleyicilerde araç ipuçları bu açıklamaları çağrı sitesinde görüntüleyebilen [XML belge açıklamalarını](../language-reference/xml-documentation.md) kullanmaktır. Kodunuzun, araçları ile diğer programcılar tarafından nasıl okunacağını, gezindiği, hata ayıklayacağını ve nasıl değiştirileceğini her zaman düşünün.

## <a name="next-steps"></a>Sonraki adımlar

[F # kod biçimlendirme yönergeleri](formatting.md) , kodun okunması kolay olacak şekilde nasıl biçimlendirilebileceğine ilişkin yönergeler sağlar.

[F # kodlama kuralları](conventions.md) , büyük f # codeesaslarını uzun süreli bakımın sağlanmasına yardımcı olacak f # programlama deyimidir OMS için rehberlik sağlar.

[F # bileşeni tasarım yönergeleri](component-design-guidelines.md) , kitaplıklar gibi f # bileşenleri yazmak için rehberlik sağlar.
