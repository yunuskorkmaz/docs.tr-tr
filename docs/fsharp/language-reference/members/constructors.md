---
title: Oluşturucular (F#)
description: "Tanımlayın ve oluşturucular F #'ta oluşturmak ve sınıf ve yapısı nesneleri başlatmak için nasıl kullanılacağını öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: d9062ae747c37bdc14104658ad0ec7d11f5545f0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="constructors"></a>Oluşturucular

Bu konu, tanımlama ve oluşturma ve sınıf ve yapısı nesneleri başlatma için oluşturucular kullanma açıklar.


## <a name="construction-of-class-objects"></a>Sınıf nesnelerine yapımı
Sınıf türleri nesnelerin oluşturucular vardır. Oluşturucular iki tür vardır. Parametreleri yalnızca tür adından sonra parantez içinde görünür birincil Oluşturucusu biridir. Diğer, isteğe bağlı ek oluşturucuları kullanarak belirttiğiniz `new` anahtar sözcüğü. Böyle bir ek oluşturucular birincil Oluşturucusu çağırmanız gerekir.

Birincil Oluşturucuyu içeren `let` ve `do` sınıf tanımını başlangıcında görünür bağlar. A `let` bağlama bildirir özel alanlar ve; sınıfı yöntemlerinin bir `do` bağlama kodu yürütür. Hakkında daha fazla bilgi için `let` sınıfı Yapıcılardaki bağlamaları bkz [ `let` sınıflardaki bağlamaları](let-bindings-in-classes.md). Hakkında daha fazla bilgi için `do` Oluşturucular, bağlama bkz [ `do` sınıflardaki bağlamaları](do-bindings-in-classes.md).

Çağrı istediğiniz Oluşturucusu birincil oluşturucu veya ek bir oluşturucu olup olmadığına bakılmaksızın, nesneleri kullanarak oluşturabileceğiniz bir `new` ifadesi, ile veya isteğe bağlı olmadan `new` anahtar sözcüğü. Virgülle ayrılmış nesnelerinizi oluşturucu bağımsız değişkenleri, sipariş değişkenlerinde listesi ile birlikte başlatmak ve parantez içinde ya da parantez içinde adlandırılmış bağımsız değişkenler ve değerleri kullanarak içine alınmalıdır. Ayrıca özellikleri bir nesne üzerinde nesne oluşturma sırasında özellik adlarını kullanarak ayarlayabilirsiniz ve yalnızca kullandığınız gibi değerler atama adlı oluşturucu bağımsız değişkenleri.

Aşağıdaki kod bir oluşturucu ve nesneleri oluşturma çeşitli şekillerde olan bir sınıfı gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Çıktı aşağıdaki gibidir:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Yapıları yapımı
Yapıları sınıflarının tüm kuralları izleyin. Bu nedenle, birincil bir oluşturucuya sahip olabilir ve kullanarak ek oluşturucular sağlayabilirsiniz `new`. Ancak, yapılar ve sınıflar arasında önemli bir fark yoktur: birincil bir oluşturucu yok tanımlanan olsa bile, yapıları varsayılan bir oluşturucu (diğer bir deyişle, bir bağımsız değişken içermeyen) sahip olabilir. Varsayılan Oluşturucu tüm alanları varsayılan değer türü, genellikle sıfır veya eşdeğer başlatır. Varsayılan Oluşturucu ile çakışmadığından emin yapıları için tanımladığınız oluşturucular en az bir değişken olmalıdır.

Ayrıca, yapıları kullanılarak oluşturulan alanları genellikle sahip `val` anahtar sözcüğü; sınıfları Ayrıca bu alanlar vardır. Yapılar ve alanlar kullanılarak tanımlanmış sınıfları `val` anahtar sözcüğü de başlatılabilir ek kurucularda kayıt ifadeler kullanarak aşağıdaki kodda gösterildiği gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Daha fazla bilgi için bkz: [açık alanlar: `val` anahtar sözcüğü](explicit-fields-the-val-keyword.md).


## <a name="executing-side-effects-in-constructors"></a>Oluşturucularda yan etkileri yürütme
Bir sınıf birincil oluşturucuda kod yürütebilir bir `do` bağlama. Ancak, yoksa ne kod ek bir oluşturucu olmadan yürütmek bir `do` bağlama? Bunu yapmak için kullandığınız `then` anahtar sözcüğü.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Birincil Oluşturucusu yan etkileri hala yürütün. Bu nedenle, çıktı şu şekildedir.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Yapıcılardaki kendine yönelik tanımlayıcılar
Diğer üyeler her üye tanımı geçerli nesne için bir ad sağlayın. Kullanarak sınıf tanımının ilk satırda kendini tanımlayıcı koyabilirsiniz `as` hemen Oluşturucu parametreleri aşağıdaki anahtar sözcüğü. Aşağıdaki örnekte bu söz dizimini gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Ek kurucularda da kendi kendine tanımlayıcı koyarak tanımlayabilirsiniz `as` Oluşturucu parametreleri hemen sonra yan tümcesi. Aşağıdaki örnekte bu söz dizimini gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Tam olarak tanımlanmadan önce bir nesne kullanmaya çalıştığınızda sorunları ortaya çıkabilir. Bu nedenle, kendini tanımlayıcı kullanımlarını bir uyarı yayma ve nesne başlatılmadan önce bir nesnenin üyelerine erişilemeyen emin olmak için ek denetimler eklemek derleyici neden olabilir. Yalnızca kendi kendine tanımlayıcıda kullanması gereken `do` bağlamaları birincil oluşturucunun ya da sonra `then` ek oluşturucular anahtar sözcük.

Kendi kendine tanımlayıcı adı olması gerekmez `this`. Geçerli bir tanımlayıcı olabilir.


## <a name="assigning-values-to-properties-at-initialization"></a>Başlatma sırasında özelliklerine değerler atama
Formun atamaları listesini ekleyerek başlatma kodda bir sınıf nesnesinin özellikleri için değer atayabilirsiniz `property = value` bir oluşturucu bağımsız değişken listesi. Bu, aşağıdaki kod örneğinde gösterilir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Önceki kod aşağıdaki sürümü sıradan bağımsız değişkenler, isteğe bağlı bağımsız değişkenler ve bir oluşturucu çağrısı özelliği ayarlarında birleşimi gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a>Devralınan bir sınıf oluşturucuları
Bir oluşturucuya sahip bir taban sınıftan devralınırken devral yan tümcesinde bağımsız değişkenleri belirtmeniz gerekir. Daha fazla bilgi için bkz: [oluşturucular ve devralma](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statik oluşturucular veya türü oluşturucuları
Nesneleri, statik oluşturmak için kodu belirtme yanı sıra `let` ve `do` bağlamaları yazılan türü ilk başlatma türü düzeyinde gerçekleştirmek için kullanılmadan önce yürütme sınıfı türlerinde. Daha fazla bilgi için bkz: [ `let` sınıflardaki bağlamaları](let-bindings-in-classes.md) ve [ `do` sınıflardaki bağlamaları](do-bindings-in-classes.md).

## <a name="see-also"></a>Ayrıca Bkz.
[Üyeler](index.md)
