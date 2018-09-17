---
title: Oluşturucular (F#)
description: 'Tanımlamak ve oluşturucular F # oluşturup sınıfı ve yapı nesneleri için kullanma hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: ff2463f890034cce0bbaa85d9a5c93e50427cd03
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743923"
---
# <a name="constructors"></a>Oluşturucular

Bu konu, oluşturmak ve sınıf ve yapı nesneleri için oluşturucu tanımlanacağını ve kullanılacağını açıklar.

## <a name="construction-of-class-objects"></a>Sınıf nesnelerine yapımı

Sınıf türü nesneleri oluşturuculara sahip. Oluşturucular iki tür vardır. Parametreleri yalnızca tür adından sonra parantez içinde görünmesi birincil Oluşturucusu biridir. Diğer, isteğe bağlı ek oluşturucuları kullanarak belirttiğiniz `new` anahtar sözcüğü. Böyle bir ek oluşturucular birincil Oluşturucu çağırmanız gerekir.

Birincil kurucu içeriyorsa `let` ve `do` sınıf tanımının başlangıcında görünür bağlar. A `let` bağlama bildirir özel alanlar ve yöntemler sınıf; bir `do` bağlama kodu yürütür. Hakkında daha fazla bilgi için `let` sınıfı Yapıcılardaki bağlamaları görmek [ `let` sınıflardaki bağlamaları](let-bindings-in-classes.md). Hakkında daha fazla bilgi için `do` , oluşturucularda bağlamaları görmek [ `do` sınıflardaki bağlamaları](do-bindings-in-classes.md).

Oluşturucu çağırmak istediğiniz birincil bir oluşturucu veya ek bir oluşturucuda olup olmadığına bakılmaksızın, nesneleri kullanarak oluşturabileceğiniz bir `new` ifade, içeren veya içermeyen isteğe bağlı `new` anahtar sözcüğü. Virgülle ayırarak oluşturucu bağımsız değişkenleri, bağımsız değişken listesi ile birlikte, nesneleri ve parantez içinde adlandırılmış bağımsız değişkenler ve değerleri kullanarak veya parantez içine alınmış. Ayrıca özellikleri bir nesne üzerinde nesne oluşturma sırasında özellik adlarını kullanarak ayarlayabilirsiniz ve yalnızca kullandığınız gibi değerler atama adlı oluşturucu bağımsız değişkenleri.

Aşağıdaki kod, bir oluşturucu ve nesneleri oluşturmak için çeşitli yöntemler sahip bir sınıfı gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Çıktı aşağıdaki gibidir:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Yapıları oluşturma

Yapıları sınıflarının tüm kuralları uygulayın. Bu nedenle, birincil bir oluşturucuya sahip olabilir ve ek oluşturucuları kullanarak sağlayabilirsiniz `new`. Ancak, yapılar ve sınıflar arasında önemli bir fark yoktur: yapıları birincil hiçbir oluşturucu tanımlansa bile bir varsayılan Oluşturucusu (diğer bir deyişle, bir bağımsız değişken olmadan) sahip olabilir. Varsayılan Oluşturucu tüm alanları varsayılan değer türü, genellikle sıfır ya da eşdeğerine başlatır. Varsayılan Oluşturucu ile çakışmadığından emin yapıları için tanımladığınız tüm oluşturucular en az bir bağımsız değişken olmalıdır.

Ayrıca, yapıları kullanılarak oluşturulan alanlar genellikle sahip `val` anahtar sözcüğü; sınıfları bu alanlar da içerebilir. Yapılar ve sınıflar tarafından tanımlanan alanlara sahip `val` anahtar sözcüğü de başlatılabilir ek oluşturucularda kayıt ifadelerini kullanarak aşağıdaki kodda gösterildiği gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Daha fazla bilgi için [açık alanlar: `val` anahtar sözcüğü](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Oluşturucularda yan etkileri yürütülüyor

Birincil bir oluşturucu bir sınıftaki kod yürütebilir bir `do` bağlama. Ancak, varsa ne olmadan kod ek bir oluşturucuda, yürütülecek bir `do` bağlama? Bunu yapmak için kullandığınız `then` anahtar sözcüğü.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Birincil Oluşturucusu yan etkilerini hala yürütün. Bu nedenle, çıkış aşağıdaki gibidir.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Oluşturucularda kendine yönelik tanımlayıcılar

Diğer üyeleri, her üyesinin tanımındaki geçerli nesne için bir ad sağlayın. Kullanarak sınıf tanımının ilk satıra kendini tanımlayıcısı koyabilirsiniz `as` Oluşturucu parametresi takip anahtar sözcüğü. Aşağıdaki örnek bu söz dizimini gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Ek oluşturucularda de kendi kendine bir tanımlayıcı koyarak tanımlayabilirsiniz `as` Oluşturucu parametresi hemen sonra yan tümcesi. Aşağıdaki örnek bu söz dizimini gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Tam olarak tanımlanmadan önce bir nesne kullanmaya çalıştığınızda sorunlar oluşabilir. Bu nedenle, kendi kendine tanımlayıcı kullanımlarını, derleyici bir uyarı verir ve nesne başlatılmadan önce bir nesnenin üyelerine erişilemeyen emin olmak için ek denetimler eklemek neden olabilir. Yalnızca kendi kendine tanımlayıcıda kullanmalısınız `do` bağlamaları birincil oluşturucunun ya da sonra `then` ek Yapıcılardaki anahtar sözcüğü.

Kendi kendine tanımlayıcı adı olmak zorunda değil `this`. Bu, herhangi bir geçerli tanımlayıcı olabilir.

## <a name="assigning-values-to-properties-at-initialization"></a>Başlatma sırasında özelliklere değerler atama

Formun atamaları listesini ekleyerek başlatma kodu sınıf nesnesinde özelliklerine değerler atayabilirsiniz `property = value` bir oluşturucu için bağımsız değişken listesi. Bu aşağıdaki kod örneğinde gösterilir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Önceki kod aşağıdaki sürümü sıradan bağımsız değişkenler, isteğe bağlı bağımsız değişkenler ve özellik ayarlarını bir oluşturucu çağrısı birleşimi gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Devralınan sınıf oluşturucular

Bir oluşturucuya sahip bir taban sınıftan devralınırken devral yan tümcesinde bağımsız değişkenleri belirtmeniz gerekir. Daha fazla bilgi için [oluşturucular ve devralma](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statik oluşturucular veya tür Oluşturucu

Statik nesneler oluşturmak için kod belirtme yanı sıra `let` ve `do` bağlamaları yazılan türünü ilk tür düzeyinde başlatma gerçekleştirmek için kullanılmadan önce yürütülen sınıf türleri. Daha fazla bilgi için [ `let` sınıflardaki bağlamaları](let-bindings-in-classes.md) ve [ `do` sınıflardaki bağlamaları](do-bindings-in-classes.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
