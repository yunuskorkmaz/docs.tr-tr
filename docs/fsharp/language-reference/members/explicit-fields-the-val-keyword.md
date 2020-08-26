---
title: 'Açık Alanlar: val Anahtar Sözcüğü'
description: "Türü başlatmadan bir sınıf veya yapı türünde bir değeri depolamak üzere bir konum bildirmek için kullanılan F # ' Val ' anahtar sözcüğü hakkında bilgi edinin."
ms.date: 08/15/2020
ms.openlocfilehash: 9f5599a241f27b234eeacf48327b4ccbc46ed38c
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811788"
---
# <a name="explicit-fields-the-val-keyword"></a>Açık Alanlar: val Anahtar Sözcüğü

`val`Anahtar sözcüğü, bir değeri, bir sınıf veya yapı türünde depolayacak bir konum bildirmek için kullanılır. Bu şekilde belirtilen depolama konumlarına *açık alanlar*denir. Anahtar sözcüğünün başka bir kullanımı, `val` `member` otomatik olarak uygulanan bir özelliği bildirmek için anahtar kelimesiyle birlikte bulunur. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [Özellikler](properties.md).

## <a name="syntax"></a>Syntax

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Açıklamalar

Bir sınıf veya yapı türündeki alanları tanımlamanın olağan yolu bir `let` bağlama kullanmaktır. Ancak `let` bağlamalar, sınıf oluşturucusunun bir parçası olarak başlatılmalıdır, bu her zaman mümkün, gerekli veya istenmez. `val`Başlatılmamış bir alanı istediğiniz zaman anahtar sözcüğünü kullanabilirsiniz.

Açık Alanlar statik veya statik olmayan bir şekilde olabilir. *Erişim-değiştirici* `public` , `private` veya olabilir `internal` . Varsayılan olarak açık alanlar geneldir. Bu `let` , her zaman özel olan sınıflardaki bağlamalardan farklıdır.

[DefaultValue](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-defaultvalueattribute.html) özniteliği, birincil Oluşturucusu olan sınıf türlerindeki açık alanlar için gereklidir. Bu öznitelik, alanın sıfıra başlatıldığını belirtir. Alanın türü sıfır başlatmayı desteklemelidir. Bir tür, aşağıdakilerden biri ise sıfır başlatmayı destekler:

- Sıfır değeri olan temel bir tür.
- Normal değer olarak, olağan dışı bir değer olarak veya bir değerin temsili olarak null değeri destekleyen bir tür. Bu sınıflar, tanımlama grupları, kayıtlar, işlevler, arabirimler, .NET başvuru türleri, `unit` türü ve ayırt edici birleşim türlerini içerir.
- .NET değer türü.
- Alanlarının tümü varsayılan sıfır değerini destekleyen bir yapı.

Örneğin, adlı bir sabit alan, `someField` .NET derlenmiş temsilinin adına sahip bir yedekleme alanına sahiptir `someField@` ve depolanan değere adlı bir özellik kullanarak erişirsiniz `someField` .

Kesilebilir bir alan için, .NET derlenmiş gösterimi .NET alanıdır.

> [!WARNING]
> .NET Framework ad alanı `System.ComponentModel` aynı ada sahip bir özniteliği içeriyor. Bu öznitelik hakkında daha fazla bilgi için bkz <xref:System.ComponentModel.DefaultValueAttribute> ..

Aşağıdaki kod açık alanların kullanımını ve karşılaştırma için, `let` birincil Oluşturucusu olan bir sınıftaki bağlamayı gösterir. `let`-Bağlanacak alanın özel olduğunu unutmayın `myInt1` . `let` `myInt1` Bir üye yönteminden bağlantılı alana başvuruluyorsa, kendi tanımlayıcısı `this` gerekli değildir. Ancak açık alanlara başvururken `myInt2` `myString` , kendi tanımlayıcısı gereklidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
11 12 abc
30 def
```

Aşağıdaki kod, birincil Oluşturucusu olmayan bir sınıfta açık alanların kullanımını gösterir. Bu durumda, `DefaultValue` öznitelik gerekli değildir, ancak tüm alanların tür için tanımlanan oluşturucularda başlatılmış olması gerekir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Çıktı `35 22` olur.

Aşağıdaki kod, bir yapıda açık alanların kullanımını gösterir. Bir yapı bir değer türü olduğundan, alanlarının değerlerini sıfıra ayarlayan parametresiz bir oluşturucuya otomatik olarak sahiptir. Bu nedenle, `DefaultValue` öznitelik gerekli değildir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Çıktı `11 xyz` olur.

**Dikkat**edin, yapınızı `mutable` anahtar sözcük içermeyen alanlarla başlatacaksanız `mutable` , atamalarınız, atamadan sonra atılacak yapının bir kopyası üzerinde çalışır. Bu nedenle, yapınız değişmeyecek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Açık alanlar, rutin kullanım için tasarlanmamıştır. Genel olarak, mümkün olduğunda `let` açık bir alan yerine sınıfında bir bağlama kullanmanız gerekir. Açık alanlar, yerel API 'ye yönelik platform çağırma çağrısında veya COM birlikte çalışma senaryolarında kullanılacak bir yapı tanımlamanız gerektiğinde olduğu gibi, belirli birlikte çalışabilirlik senaryolarında yararlıdır. Daha fazla bilgi için bkz. [dış işlevler](../functions/external-functions.md). Bir açık alanın gerekli olabileceği başka bir durum ise, sınıfları birincil Oluşturucu olmadan yayar bir F # kod oluşturucusuyla çalışırken olur. Açık alanlar, iş parçacığı statik değişkenleri veya benzer yapılar için de kullanışlıdır. Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.

Anahtar sözcükler `member val` bir tür tanımında birlikte görüntülendiğinde, otomatik olarak uygulanan bir özelliğin tanımıdır. Daha fazla bilgi için bkz. [Özellikler](properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](properties.md)
- [Üyeler](index.md)
- [`let` Sınıflarda bağlamalar](let-bindings-in-classes.md)
