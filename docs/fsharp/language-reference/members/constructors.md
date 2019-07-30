---
title: Oluşturucular
description: Sınıf ve yapı nesneleri oluşturmak ve başlatmak için F# ' de oluşturucuları tanımlama ve kullanma hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: c25fdcb95c2873eb69a94f30c87735e5c04d391b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627602"
---
# <a name="constructors"></a>Oluşturucular

Bu konuda, sınıf ve yapı nesneleri oluşturmak ve başlatmak için oluşturucuların nasıl tanımlanacağı ve kullanılacağı açıklanmaktadır.

## <a name="construction-of-class-objects"></a>Sınıf nesnelerinin oluşturulması

Sınıf türündeki nesnelerin oluşturucuları vardır. İki tür Oluşturucu vardır. Bunlardan biri, tür adından hemen sonra, parametreleri parantez içinde görüntülenen birincil oluşturucudur. `new` Anahtar sözcüğünü kullanarak diğer, isteğe bağlı ek oluşturucular belirtirsiniz. Bu tür ek oluşturucuların birincil oluşturucuyu çağırması gerekir.

Birincil Oluşturucu, sınıf `let` tanımının `do` başlangıcında görüntülenen bağlamaları ve içerir. Bağlama, sınıfın özel alanlarını ve yöntemlerini bildirir; bir `do` bağlama kodu yürütür. `let` Sınıf oluşturucularında bağlamalar `let` hakkında daha fazla bilgi için bkz [ `let` . sınıflarda bağlamalar](let-bindings-in-classes.md). Oluşturuculardaki bağlamalar hakkında `do` daha fazla bilgi için bkz [ `do` . sınıflarda bağlamalar](do-bindings-in-classes.md).

Çağırmak istediğiniz oluşturucunun birincil Oluşturucu mı yoksa ek bir Oluşturucu mı olduğuna bakılmaksızın, isteğe bağlı `new` `new` anahtar sözcüğü ile veya olmadan bir ifadesi kullanarak nesneler oluşturabilirsiniz. Bağımsız değişkenleri sırayla listeleyerek ve virgülle ayırarak ya da parantez içinde adlandırılmış bağımsız değişkenleri ve değerleri kullanarak, nesnelerinizi Oluşturucu bağımsız değişkenlerle birlikte başlatabilirsiniz. Ayrıca, özellik adlarını kullanarak ve yalnızca adlandırılmış Oluşturucu bağımsız değişkenleri kullandığınız gibi değer atayarak nesne oluşturma sırasında nesne üzerinde özellikler ayarlayabilirsiniz.

Aşağıdaki kod, Oluşturucusu olan bir sınıfı ve nesne oluşturmanın çeşitli yollarını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Çıktı aşağıdaki gibidir:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Yapıların oluşturulması

Yapılar sınıfların tüm kurallarını izler. Bu nedenle, bir birincil oluşturucuya sahip olabilirsiniz ve kullanarak `new`ek oluşturucular sağlayabilirsiniz. Ancak, yapılar ve sınıflar arasında önemli bir farklılık vardır: yapılar, hiçbir birincil Oluşturucu tanımlanmasa bile parametresiz bir oluşturucuya (bağımsız değişken içermeyen bir) sahip olabilir. Parametresiz Oluşturucu, tüm alanları bu tür için varsayılan değere (genellikle sıfır veya eşdeğeri) başlatır. Yapılar için tanımladığınız tüm oluşturucuların en az bir bağımsız değişkeni olması gerekir, bu nedenle varsayılan Oluşturucu ile çakışamazlar.

Ayrıca, yapılar genellikle `val` anahtar sözcüğü kullanılarak oluşturulan alanlara sahiptir; sınıflar da bu alanları içerebilir. `val` Anahtar sözcüğü kullanılarak tanımlanmış olan yapılar ve sınıflar, aşağıdaki kodda gösterildiği gibi, kayıt ifadeleri kullanılarak ek oluşturuculara de başlatılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Daha fazla bilgi için bkz [. açık alanlar: `val` Anahtar sözcüğü](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Oluşturucularda yan etkileri yürütme

Bir sınıftaki birincil Oluşturucu, bir `do` bağlamadaki kodu yürütebilir. Ancak, bir `do` bağlama olmadan kodu ek bir oluşturucuda yürütmeniz gerekiyorsa ne yapmanız gerekir? Bunu yapmak için `then` anahtar sözcüğünü kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Birincil oluşturucunun yan etkileri hala yürütülür. Bu nedenle, çıkış aşağıdaki gibidir.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Oluşturucularda kendi tanımlayıcıları

Diğer üyelerde, her üyenin tanımında geçerli nesne için bir ad sağlarsınız. Ayrıca, Oluşturucu parametrelerinin hemen ardından gelen `as` anahtar sözcüğünü kullanarak sınıf tanımının ilk satırına kendi tanımlayıcısını koyabilirsiniz. Aşağıdaki örnekte bu söz dizimi gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Ek oluşturucularda, `as` yan tümcesini Oluşturucu parametrelerinden sonra koyarak kendi kendine tanımlayıcıyı da tanımlayabilirsiniz. Aşağıdaki örnekte bu söz dizimi gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Bir nesne, tam olarak tanımlanmadan önce kullanmaya çalıştığınızda sorunlar oluşabilir. Bu nedenle, kendi kendine tanımlayıcı kullanımları derleyicinin bir uyarı yaymasına ve nesne başlatılmadan önce bir nesnenin üyelerine erişilmemesini sağlamak için ek denetimler eklemesine neden olabilir. Self tanımlayıcıyı `do` yalnızca birincil oluşturucunun bağlamalarında veya ek oluşturuculardaki `then` anahtar sözcükten sonra kullanmanız gerekir.

Kendi tanımlayıcısının adının olması `this`gerekmez. Geçerli bir tanımlayıcı olabilir.

## <a name="assigning-values-to-properties-at-initialization"></a>Başlatma sırasında özelliklere değerler atama

Bir oluşturucunun bağımsız değişken listesine form `property = value` atamalarının bir listesini ekleyerek başlatma kodundaki bir sınıf nesnesinin özelliklerine değerler atayabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Önceki kodun aşağıdaki sürümü, tek bir Oluşturucu çağrısında sıradan bağımsız değişkenlerin, isteğe bağlı bağımsız değişkenlerin ve özellik ayarlarının birleşimini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Devralınan sınıftaki oluşturucular

Oluşturucusu olan bir taban sınıftan devralınırken, devralma yan tümcesinde bağımsız değişkenlerini belirtmeniz gerekir. Daha fazla bilgi için bkz. [oluşturucular ve devralma](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statik oluşturucular veya tür oluşturucuları

Nesne oluşturmaya yönelik kodu belirtmenin yanı sıra, statik `let` ve `do` bağlamalar tür düzeyinde başlatma gerçekleştirmek için önce yürütülen sınıf türlerinde yazılabilir. Daha fazla bilgi için [ `do` ](do-bindings-in-classes.md)bkz [ `let` ](let-bindings-in-classes.md) . sınıflardaki sınıflarda ve bağlamalardaki bağlamalar.

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
