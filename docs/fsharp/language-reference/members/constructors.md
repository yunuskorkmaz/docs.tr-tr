---
title: Oluşturucular
description: "F # ' da sınıf ve yapı nesneleri oluşturmak ve başlatmak için oluşturucuları tanımlama ve kullanma hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303445"
---
# <a name="constructors"></a>Oluşturucular

Bu makalede, sınıf ve yapı nesneleri oluşturmak ve başlatmak için oluşturucuların nasıl tanımlanacağı ve kullanılacağı açıklanmaktadır.

## <a name="construction-of-class-objects"></a>Sınıf nesnelerinin oluşturulması

Sınıf türündeki nesnelerin oluşturucuları vardır. İki tür Oluşturucu vardır. Bunlardan biri, tür adından hemen sonra, parametreleri parantez içinde görüntülenen birincil oluşturucudur. Anahtar sözcüğünü kullanarak diğer, isteğe bağlı ek oluşturucular belirtirsiniz `new` . Bu tür ek oluşturucuların birincil oluşturucuyu çağırması gerekir.

Birincil Oluşturucu, `let` `do` sınıf tanımının başlangıcında görüntülenen bağlamaları ve içerir. `let`Bağlama, sınıfın özel alanlarını ve yöntemlerini bildirir; bir `do` bağlama kodu yürütür. Sınıf oluşturucularında bağlamalar hakkında daha fazla bilgi için `let` bkz. [ `let` sınıflarda bağlamalar](let-bindings-in-classes.md). Oluşturuculardaki bağlamalar hakkında daha fazla bilgi için `do` bkz. [ `do` sınıflarda bağlamalar](do-bindings-in-classes.md).

Çağırmak istediğiniz oluşturucunun birincil Oluşturucu mı yoksa ek bir Oluşturucu mı olduğuna bakılmaksızın, `new` isteğe bağlı anahtar sözcüğü ile veya olmadan bir ifadesi kullanarak nesneler oluşturabilirsiniz `new` . Bağımsız değişkenleri sırayla listeleyerek ve virgülle ayırarak ya da parantez içinde adlandırılmış bağımsız değişkenleri ve değerleri kullanarak, nesnelerinizi Oluşturucu bağımsız değişkenlerle birlikte başlatabilirsiniz. Ayrıca, özellik adlarını kullanarak ve yalnızca adlandırılmış Oluşturucu bağımsız değişkenleri kullandığınız gibi değer atayarak nesne oluşturma sırasında nesne üzerinde özellikler ayarlayabilirsiniz.

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

Yapılar sınıfların tüm kurallarını izler. Bu nedenle, bir birincil oluşturucuya sahip olabilirsiniz ve kullanarak ek oluşturucular sağlayabilirsiniz `new` . Ancak, yapılar ve sınıflar arasında önemli bir farklılık vardır: yapılar, hiçbir birincil Oluşturucu tanımlanmasa bile parametresiz bir oluşturucuya (bağımsız değişken içermeyen bir) sahip olabilir. Parametresiz Oluşturucu, tüm alanları bu tür için varsayılan değere (genellikle sıfır veya eşdeğeri) başlatır. Yapılar için tanımladığınız tüm oluşturucular, parametresiz oluşturucuyla çakışmayacak şekilde en az bir bağımsız değişkene sahip olmalıdır.

Ayrıca, yapılar genellikle anahtar sözcüğü kullanılarak oluşturulan alanlara sahiptir `val` ; sınıflar da bu alanları içerebilir. Anahtar sözcüğü kullanılarak tanımlanmış olan yapılar ve sınıflar `val` , aşağıdaki kodda gösterildiği gibi, kayıt ifadeleri kullanılarak ek oluşturuculara de başlatılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Daha fazla bilgi için bkz. [açık alanlar: `val` anahtar sözcük](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Oluşturucularda yan etkileri yürütme

Bir sınıftaki birincil Oluşturucu, bir `do` bağlamadaki kodu yürütebilir. Ancak, bir bağlama olmadan kodu ek bir oluşturucuda yürütmeniz gerekiyorsa ne yapmanız gerekir `do` ? Bunu yapmak için `then` anahtar sözcüğünü kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Birincil oluşturucunun yan etkileri hala yürütülür. Bu nedenle, çıkış aşağıdaki gibidir:

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

Bunun yerine neden gerekli olmasının nedeni, `then` `do` `do` anahtar sözcüğünün, `unit` ek bir oluşturucunun gövdesinde mevcut olduğunda, bir döndüren ifadenin standart anlamı vardır. Birincil oluşturucuların bağlamında yalnızca özel anlamı vardır.

## <a name="self-identifiers-in-constructors"></a>Oluşturucularda kendi tanımlayıcıları

Diğer üyelerde, her üyenin tanımında geçerli nesne için bir ad sağlarsınız. Ayrıca, `as` Oluşturucu parametrelerinin hemen ardından gelen anahtar sözcüğünü kullanarak sınıf tanımının ilk satırına kendi tanımlayıcısını koyabilirsiniz. Aşağıdaki örnekte bu söz dizimi gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Ek oluşturucularda, `as` yan tümcesini Oluşturucu parametrelerinden sonra koyarak kendi kendine tanımlayıcıyı da tanımlayabilirsiniz. Aşağıdaki örnekte bu söz dizimi gösterilmektedir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Bir nesne, tam olarak tanımlanmadan önce kullanmaya çalıştığınızda sorunlar oluşabilir. Bu nedenle, kendi kendine tanımlayıcı kullanımları derleyicinin bir uyarı yaymasına ve nesne başlatılmadan önce bir nesnenin üyelerine erişilmemesini sağlamak için ek denetimler eklemesine neden olabilir. Self tanımlayıcıyı yalnızca `do` birincil oluşturucunun bağlamalarında veya `then` ek oluşturuculardaki anahtar sözcükten sonra kullanmanız gerekir.

Kendi tanımlayıcısının adının olması gerekmez `this` . Geçerli bir tanımlayıcı olabilir.

## <a name="assigning-values-to-properties-at-initialization"></a>Başlatma sırasında özelliklere değerler atama

Bir oluşturucunun bağımsız değişken listesine form atamalarının bir listesini ekleyerek başlatma kodundaki bir sınıf nesnesinin özelliklerine değerler atayabilirsiniz `property = value` . Bu, aşağıdaki kod örneğinde gösterilmektedir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Önceki kodun aşağıdaki sürümü, tek bir Oluşturucu çağrısında sıradan bağımsız değişkenlerin, isteğe bağlı bağımsız değişkenlerin ve özellik ayarlarının birleşimini gösterir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Devralınan sınıftaki oluşturucular

Oluşturucusu olan bir taban sınıftan devralınırken, devralma yan tümcesinde bağımsız değişkenlerini belirtmeniz gerekir. Daha fazla bilgi için bkz. [oluşturucular ve devralma](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statik oluşturucular veya tür oluşturucuları

Nesne oluşturmaya yönelik kodu belirtmenin yanı sıra, statik `let` ve `do` bağlamalar tür düzeyinde başlatma gerçekleştirmek için önce yürütülen sınıf türlerinde yazılabilir. Daha fazla bilgi için bkz. sınıflardaki [ `let` sınıflarda ve bağlamalardaki bağlamalar](let-bindings-in-classes.md) . [ `do` ](do-bindings-in-classes.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
