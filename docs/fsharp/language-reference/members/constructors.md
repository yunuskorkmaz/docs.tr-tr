---
title: Kurucu
description: Sınıf ve yapı nesneleri oluşturmak ve başlatmak için F# ' de oluşturucuları tanımlama ve kullanma hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 6769ec7fc6768090d8ae68e21946a58829b6eea0
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736844"
---
# <a name="constructors"></a>Kurucu

Bu makalede, sınıf ve yapı nesneleri oluşturmak ve başlatmak için oluşturucuların nasıl tanımlanacağı ve kullanılacağı açıklanmaktadır.

## <a name="construction-of-class-objects"></a>Sınıf nesnelerinin oluşturulması

Sınıf türündeki nesnelerin oluşturucuları vardır. İki tür Oluşturucu vardır. Bunlardan biri, tür adından hemen sonra, parametreleri parantez içinde görüntülenen birincil oluşturucudur. @No__t-0 anahtar sözcüğünü kullanarak diğer, isteğe bağlı ek oluşturucular belirlersiniz. Bu tür ek oluşturucuların birincil oluşturucuyu çağırması gerekir.

Birincil Oluşturucu, sınıf tanımının başlangıcında görüntülenen `let` ve `do` bağlamaları içerir. @No__t-0 bağlaması, sınıfın özel alanlarını ve yöntemlerini bildirir; `do` bağlama kodu yürütür. Sınıf oluşturucularında `let` bağlamaları hakkında daha fazla bilgi için bkz. [sınıflarda `let` bağlamaları](let-bindings-in-classes.md). Oluşturucularda `do` bağlamaları hakkında daha fazla bilgi için bkz. [sınıflarda `do` bağlamaları](do-bindings-in-classes.md).

Çağırmak istediğiniz oluşturucunun birincil Oluşturucu mı yoksa ek bir Oluşturucu mı olduğuna bakılmaksızın, isteğe bağlı `new` anahtar sözcüğüyle veya olmadan `new` ifadesi kullanarak nesneler oluşturabilirsiniz. Bağımsız değişkenleri sırayla listeleyerek ve virgülle ayırarak ya da parantez içinde adlandırılmış bağımsız değişkenleri ve değerleri kullanarak, nesnelerinizi Oluşturucu bağımsız değişkenlerle birlikte başlatabilirsiniz. Ayrıca, özellik adlarını kullanarak ve yalnızca adlandırılmış Oluşturucu bağımsız değişkenleri kullandığınız gibi değer atayarak nesne oluşturma sırasında nesne üzerinde özellikler ayarlayabilirsiniz.

Aşağıdaki kod, Oluşturucusu olan bir sınıfı ve nesne oluşturmanın çeşitli yollarını gösterir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Yapıların oluşturulması

Yapılar sınıfların tüm kurallarını izler. Bu nedenle, bir birincil oluşturucuya sahip olabilirsiniz ve `new` kullanarak ek oluşturucular sağlayabilirsiniz. Ancak, yapılar ve sınıflar arasında önemli bir farklılık vardır: yapılar, hiçbir birincil Oluşturucu tanımlanmasa bile parametresiz bir oluşturucuya (bağımsız değişken içermeyen bir) sahip olabilir. Parametresiz Oluşturucu, tüm alanları bu tür için varsayılan değere (genellikle sıfır veya eşdeğeri) başlatır. Yapılar için tanımladığınız tüm oluşturucular, parametresiz oluşturucuyla çakışmayacak şekilde en az bir bağımsız değişkene sahip olmalıdır.

Ayrıca, yapılar genellikle `val` anahtar sözcüğü kullanılarak oluşturulan alanlara sahiptir; sınıflarda da bu alanlar bulunabilir. @No__t-0 anahtar sözcüğü kullanılarak tanımlanmış alanlara sahip yapılar ve sınıflar, aşağıdaki kodda gösterildiği gibi, kayıt ifadeleri kullanılarak ek oluşturucularda de başlatılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Daha fazla bilgi için bkz. [açık alanlar: `val` anahtar sözcüğü](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Oluşturucularda yan etkileri yürütme

Bir sınıftaki birincil Oluşturucu, `do` bağlamasında kod yürütebilir. Ancak, `do` bağlaması olmadan kodu ek bir oluşturucuda yürütmeniz gerekiyorsa ne yapabilirsiniz? Bunu yapmak için `then` anahtar sözcüğünü kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Birincil oluşturucunun yan etkileri hala yürütülür. Bu nedenle, çıkış aşağıdaki gibidir:

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Oluşturucularda kendi tanımlayıcıları

Diğer üyelerde, her üyenin tanımında geçerli nesne için bir ad sağlarsınız. Ayrıca, Oluşturucu parametrelerinden hemen sonra `as` anahtar sözcüğünü kullanarak, kendi kendine tanımlayıcıyı sınıf tanımının ilk satırına koyabilirsiniz. Aşağıdaki örnekte bu söz dizimi gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Ek oluşturucularda, Oluşturucu parametrelerinden sonra `as` yan tümcesini yerleştirerek kendi kendine tanımlayıcıyı da tanımlayabilirsiniz. Aşağıdaki örnekte bu söz dizimi gösterilmektedir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Bir nesne, tam olarak tanımlanmadan önce kullanmaya çalıştığınızda sorunlar oluşabilir. Bu nedenle, kendi kendine tanımlayıcı kullanımları derleyicinin bir uyarı yaymasına ve nesne başlatılmadan önce bir nesnenin üyelerine erişilmemesini sağlamak için ek denetimler eklemesine neden olabilir. Self tanımlayıcıyı, birincil oluşturucunun `do` bağlamalarında veya ek oluşturuculardaki `then` anahtar sözcüğünden sonra kullanmanız gerekir.

Kendi tanımlayıcısının adının `this` olması gerekmez. Geçerli bir tanımlayıcı olabilir.

## <a name="assigning-values-to-properties-at-initialization"></a>Başlatma sırasında özelliklere değerler atama

Bir oluşturucunun bağımsız değişken listesine `property = value` form atamalarının bir listesini ekleyerek başlatma kodundaki bir sınıf nesnesinin özelliklerine değerler atayabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmektedir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Önceki kodun aşağıdaki sürümü, tek bir Oluşturucu çağrısında sıradan bağımsız değişkenlerin, isteğe bağlı bağımsız değişkenlerin ve özellik ayarlarının birleşimini gösterir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Devralınan sınıftaki oluşturucular

Oluşturucusu olan bir taban sınıftan devralınırken, devralma yan tümcesinde bağımsız değişkenlerini belirtmeniz gerekir. Daha fazla bilgi için bkz. [oluşturucular ve devralma](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statik oluşturucular veya tür oluşturucuları

Nesne oluşturmaya yönelik kodu belirtmenin yanı sıra statik `let` ve `do` bağlamaları tür düzeyinde başlatma gerçekleştirmek için önce yürütülen sınıf türlerinde yazılabilir. Daha fazla bilgi için bkz. [sınıflarda `let` bağlamaları](let-bindings-in-classes.md) ve [sınıflarda `do` bağlamaları](do-bindings-in-classes.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeleri](index.md)
