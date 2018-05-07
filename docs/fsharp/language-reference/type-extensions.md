---
title: Tür Uzantıları (F#)
description: 'Önceden tanımlanmış nesne türü için yeni üye eklemek F # tür uzantıları nasıl izin öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 2181745ea75894fbfe35d5522c130baaf1876455
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-extensions"></a>Tür Uzantıları

Tür uzantıları önceden tanımlanmış nesne türü için yeni üyeler eklemenize olanak sağlar.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a>Açıklamalar
Biraz farklı bir sözdizimi ve davranış türü uzantıları iki tür vardır. Bir *iç uzantı* aynı ad alanı veya modül, aynı kaynak dosyasını ve aynı derleme (DLL ya da yürütülebilir dosya) görüntülenen genişletilen türü olarak uzantısıdır. Bir *isteğe bağlı uzantı* özgün modülü, ad veya derleme genişletilen türü dışında görünür bir uzantısıdır. İç uzantıları türüne türü tarafından yansıma incelenir, ancak isteğe bağlı uzantılar sağlamadığı görünür. Uzantıları modülleri olmalıdır ve uzantısını içeren modülü açık olduğunda bunlar yalnızca kapsamda isteğe bağlı.

Önceki sözdiziminde *typename* genişletilen türünü temsil eder. Erişilebilen herhangi bir türü genişletilmiş ancak tür adı türü kısaltması bir gerçek tür adı olmalıdır. Birden çok üye bir türü uzantısı'nda tanımlayabilirsiniz. *Kendi kendine tanımlayıcı* yalnızca normal üye olduğu gibi çağrılan nesne örneğini temsil eder.

`end` Sözcüktür basit sözdiziminde isteğe bağlıdır.

Üye türü uzantılarında tanımlanmıştır gibi diğer üyeleri bir sınıf türü üzerinde kullanılabilir. Diğer üyeleri gibi bunlar statik veya örnek üyeleri. Bu yöntemleri olarak da bilinen olan *genişletme yöntemleri*; özellikleri olarak bilinen *uzantısı özellikleri*ve benzeri. İsteğe bağlı uzantı üyeleri statik üyeleri için nesne örneği örtük olarak ilk parametre olarak geçirilen derlenir. Ancak, örnek üyelerin veya nasıl bildirilir göre statik üyeler gibi bunlar görür. Örtük uzantı üyeleri türü bir üyesi olarak dahil edilir ve kısıtlama kullanılabilir.

Genişletme yöntemleri sanal ya da soyut yöntemler olamaz. Aynı ada sahip başka yöntemler aşırı yüklenebilir, ancak derleyici tercih uzantısı olmayan yöntemlerine belirsiz bir çağrı durumunda sağlar.

Birden çok geçerli bir tür uzantıları için bir türü yoksa, tüm üyeleri benzersiz olması gerekir. İsteğe bağlı türü uzantıları için aynı türde farklı tür uzantıları üyeleri aynı ada sahip olabilir. Yalnızca istemci kodu aynı üye adlarının tanımlayan iki farklı kapsamlar açarsa belirsizlik hataları oluşur.

Aşağıdaki örnekte, geçerli bir tür uzantı modülünde bir türe sahip. Modül dışındaki istemci kodu için türü uzantısı türünün tüm bakımdan normal bir üyesi olarak görünür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

Bir tür bölümlere tanımını ayırmak için geçerli bir tür uzantıları kullanabilirsiniz. Derleyicinin ürettiği kodu ve yazılan kodu ayrı tutmak için ya da farklı kişiler tarafından oluşturulan ya da farklı işlevselliği ile ilişkili kodu gruplamak için büyük tür tanımları yönetilmesindeki yararlı olabilir.

Aşağıdaki örnekte, bir isteğe bağlı türü uzantısı genişletir `System.Int32` türü bir genişletme yöntemi ile `FromString` statik üye çağırır `Parse`. `testFromString` Yöntemi gösteren yeni üye yalnızca bir örnek üyesine gibi olarak adlandırılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

Yeni örnek üyesine herhangi diğer bir yöntemini gibi görünür `Int32` türü IntelliSense, ancak yalnızca uzantısı içeren modülü kapsamında açık veya aksi durumda olduğunda.

## <a name="generic-extension-methods"></a>Genel genişletme yöntemleri
F # 3.1 önce C# kullanımını F # derleyici desteklemekteydi-stil genel tür değişkeni, dizi türü, kayıt türü veya bir "Bu" parametresi olarak F # işlev türü ile genişletme yöntemleri. F # 3.1 Bu uzantı üyeleri kullanımını destekler.

Örneğin, F # 3.1 kodda, C# aşağıdaki söz dizimine benzer imzaları ile genişletme yöntemleri kullanabilirsiniz:

```csharp
static member Method<T>(this T input, T other)
```

Genel tür parametresi kısıtlı kullanılırken, bu yaklaşım özellikle yararlıdır. Ayrıca, artık F # kodunda şöyle uzantı üyeleri bildirme ve ek bir anlam olarak zengin genişletme yöntemleri kümesini tanımlayın. F #'ta, genellikle uzantı üyeleri aşağıdaki örnekte gösterildiği gibi tanımlayın:

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

Ancak, genel bir tür için türü değişkeni kısıtlı değil. Şimdi bir C# bildirebilirsiniz-bu sınırlamaya geçici bir çözüm için F # stili uzantı üyesi. Bu tür bir bildirimi F # satır içi özelliğiyle birleştirdiğinizde uzantısı üye olarak genel algoritmaları sunabilir.

Aşağıdaki bildirimi göz önünde bulundurun:

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Bu bildirim kullanarak, aşağıdaki örneğe benzer bir kod yazabilirsiniz.

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

Bu kodda, iki tür bir listesi için tek uzantısı üyesi tanımlayarak aşırı olmadan aynı genel aritmetik kod uygulanır.


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Üyeler](members/index.md)
