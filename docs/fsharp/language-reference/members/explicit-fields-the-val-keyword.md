---
title: 'Açık Alanlar: Val anahtar sözcüğü'
description: Türü başlatmadan bir F# sınıf veya yapı türünde bir değeri depolamak için bir konum bildirmek üzere kullanılan ' Val ' anahtar sözcüğü hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 13e0ba2875e8accfd1c0da0e1c6fef4973309f9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627537"
---
# <a name="explicit-fields-the-val-keyword"></a>Açık Alanlar: Val anahtar sözcüğü

`val` Anahtar sözcüğü, bir değeri, bir sınıf veya yapı türünde depolayacak bir konum bildirmek için kullanılır. Bu şekilde belirtilen depolama konumlarına *açık alanlar*denir. `val` Anahtar sözcüğünün başka bir kullanımı, otomatik olarak uygulanan bir `member` özelliği bildirmek için anahtar kelimesiyle birlikte bulunur. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [Özellikler](properties.md).

## <a name="syntax"></a>Sözdizimi

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Açıklamalar

Bir sınıf veya yapı türündeki alanları tanımlamanın olağan yolu bir `let` bağlama kullanmaktır. `let` Ancak bağlamalar, sınıf oluşturucusunun bir parçası olarak başlatılmalıdır, bu her zaman mümkün, gerekli veya istenmez. Başlatılmamış bir alanı istediğiniz `val` zaman anahtar sözcüğünü kullanabilirsiniz.

Açık Alanlar statik veya statik olmayan bir şekilde olabilir. *Erişim-değiştirici* , `public` `private`veya `internal`olabilir. Varsayılan olarak açık alanlar geneldir. Bu, her `let` zaman özel olan sınıflardaki bağlamalardan farklıdır.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) özniteliği, birincil Oluşturucusu olan sınıf türlerindeki açık alanlar için gereklidir. Bu öznitelik, alanın sıfıra başlatıldığını belirtir. Alanın türü sıfır başlatmayı desteklemelidir. Bir tür, aşağıdakilerden biri ise sıfır başlatmayı destekler:

- Sıfır değeri olan temel bir tür.

- Normal değer olarak, olağan dışı bir değer olarak veya bir değerin temsili olarak null değeri destekleyen bir tür. Bu sınıflar, tanımlama grupları, kayıtlar, işlevler, arabirimler, .net başvuru türleri, `unit` türü ve ayırt edici birleşim türlerini içerir.

- .NET değer türü.

- Alanlarının tümü varsayılan sıfır değerini destekleyen bir yapı.

Örneğin, adlı `someField` bir sabit alan, .NET derlenmiş temsilinin adına `someField@`sahip bir yedekleme alanına sahiptir ve depolanan değere adlı `someField`bir özellik kullanarak erişirsiniz.

Kesilebilir bir alan için, .NET derlenmiş gösterimi .NET alanıdır.

>[!WARNING]
>.NET Framework ad alanı `System.ComponentModel` aynı ada sahip bir özniteliği içeriyor. Bu öznitelik hakkında daha fazla bilgi için `System.ComponentModel.DefaultValueAttribute`bkz.

Aşağıdaki kod açık alanların kullanımını ve karşılaştırma `let` için, birincil Oluşturucusu olan bir sınıftaki bağlamayı gösterir. -Bağlanacak alanın `myInt1` özel olduğunu unutmayın. `let` Bir üye yönteminden bağlantılı alana `myInt1` başvuruluyorsa, kendi tanımlayıcısı `this` gerekli değildir. `let` Ancak açık alanlara `myInt2` `myString`başvururken, kendi tanımlayıcısı gereklidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
11 12 abc
30 def
```

Aşağıdaki kod, birincil Oluşturucusu olmayan bir sınıfta açık alanların kullanımını gösterir. Bu durumda `DefaultValue` , öznitelik gerekli değildir, ancak tüm alanların tür için tanımlanan oluşturucularda başlatılmış olması gerekir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Çıktı `35 22`.

Aşağıdaki kod, bir yapıda açık alanların kullanımını gösterir. Bir yapı bir değer türü olduğundan, kendi alanlarının değerlerini sıfıra ayarlayan bir varsayılan oluşturucuya otomatik olarak sahiptir. Bu nedenle, `DefaultValue` öznitelik gerekli değildir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Çıktı `11 xyz`.

**Dikkat**edin, yapınızı `mutable` anahtar sözcük içermeyen `mutable` alanlarla başlatacaksanız, atamalarınız, atamadan sonra atılacak yapının bir kopyası üzerinde çalışır. Bu nedenle, yapınız değişmeyecek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Açık alanlar, rutin kullanım için tasarlanmamıştır. Genel olarak, mümkün olduğunda açık bir alan yerine `let` sınıfında bir bağlama kullanmanız gerekir. Açık alanlar, yerel API 'ye yönelik platform çağırma çağrısında veya COM birlikte çalışma senaryolarında kullanılacak bir yapı tanımlamanız gerektiğinde olduğu gibi, belirli birlikte çalışabilirlik senaryolarında yararlıdır. Daha fazla bilgi için bkz. [dış işlevler](../functions/external-functions.md). Bir açık alanın gerekli olabileceği başka bir durum ise, sınıfları birincil Oluşturucu olmadan yayar bir F# kod Oluşturucu ile çalışmaktır. Açık alanlar, iş parçacığı statik değişkenleri veya benzer yapılar için de kullanışlıdır. Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.

Anahtar sözcükler `member val` bir tür tanımında birlikte görüntülendiğinde, otomatik olarak uygulanan bir özelliğin tanımıdır. Daha fazla bilgi için bkz. [Özellikler](properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](properties.md)
- [Üyeler](index.md)
- [`let`Sınıflarda bağlamalar](let-bindings-in-classes.md)
