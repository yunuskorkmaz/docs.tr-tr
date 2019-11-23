---
title: 'Açık Alanlar: val Anahtar Sözcüğü'
description: Türü başlatmadan bir F# sınıf veya yapı türünde bir değeri depolamak için bir konum bildirmek üzere kullanılan ' Val ' anahtar sözcüğü hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 2703d9a2734cfda1614a401ec24c6630ec31b2f1
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736831"
---
# <a name="explicit-fields-the-val-keyword"></a>Açık Alanlar: val Anahtar Sözcüğü

`val` anahtar sözcüğü, bir değeri bir sınıf veya yapı türünde depolayacak bir konum bildirmek için kullanılır. Bu şekilde belirtilen depolama konumlarına *açık alanlar*denir. `val` anahtar sözcüğünün başka bir kullanımı, otomatik olarak uygulanan bir özelliği bildirmek için `member` anahtar sözcüğüyle birlikte bulunur. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [Özellikler](properties.md).

## <a name="syntax"></a>Sözdizimi

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Açıklamalar

Bir sınıf veya yapı türündeki alanları tanımlamanın her zamanki yolu `let` bağlama kullanmaktır. Ancak, `let` bağlamaları sınıf oluşturucusunun bir parçası olarak başlatılmalıdır, bu her zaman mümkün değil, gerekli veya istenmez. Başlatılmamış bir alan istediğinizde `val` anahtar sözcüğünü kullanabilirsiniz.

Açık Alanlar statik veya statik olmayan bir şekilde olabilir. *Erişim-değiştirici* `public`, `private`veya `internal`olabilir. Varsayılan olarak açık alanlar geneldir. Bu, her zaman özel olan sınıflardaki `let` bağlamalarından farklıdır.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) özniteliği, birincil Oluşturucusu olan sınıf türlerindeki açık alanlar için gereklidir. Bu öznitelik, alanın sıfıra başlatıldığını belirtir. Alanın türü sıfır başlatmayı desteklemelidir. Bir tür, aşağıdakilerden biri ise sıfır başlatmayı destekler:

- Sıfır değeri olan temel bir tür.
- Normal değer olarak, olağan dışı bir değer olarak veya bir değerin temsili olarak null değeri destekleyen bir tür. Bu sınıflar, tanımlama grupları, kayıtlar, işlevler, arabirimler, .NET başvuru türleri, `unit` türü ve ayırt edici birleşim türlerini içerir.
- .NET değer türü.
- Alanlarının tümü varsayılan sıfır değerini destekleyen bir yapı.

Örneğin, `someField` adlı sabit bir alan, .NET derlenmiş gösteriminde `someField@`adı ile bir yedekleme alanı içerir ve depolanan değere `someField`adlı bir özellik kullanarak erişirsiniz.

Kesilebilir bir alan için, .NET derlenmiş gösterimi .NET alanıdır.

> [!WARNING]
> .NET Framework ad alanı `System.ComponentModel` aynı ada sahip bir özniteliği içerir. Bu öznitelik hakkında daha fazla bilgi için bkz. <xref:System.ComponentModel.DefaultValueAttribute>.

Aşağıdaki kod, açık alanların kullanımını gösterir ve birincil Oluşturucusu olan bir sınıftaki `let` bağlama için bir, karşılaştırma için. `let`bağlantılı alan `myInt1` özel olduğunu unutmayın. Bir üye yönteminden `let`bağlantılı alana `myInt1` başvuruluyorsa, kendi kendine tanımlayıcı `this` gerekli değildir. Ancak `myInt2` ve `myString`açık alanlara başvururken, kendi tanımlayıcısı gereklidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
11 12 abc
30 def
```

Aşağıdaki kod, birincil Oluşturucusu olmayan bir sınıfta açık alanların kullanımını gösterir. Bu durumda `DefaultValue` özniteliği gerekli değildir, ancak tüm alanların tür için tanımlanan oluşturucularda başlatılmış olması gerekir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Çıktı `35 22`.

Aşağıdaki kod, bir yapıda açık alanların kullanımını gösterir. Bir yapı bir değer türü olduğundan, alanlarının değerlerini sıfıra ayarlayan parametresiz bir oluşturucuya otomatik olarak sahiptir. Bu nedenle, `DefaultValue` özniteliği gerekli değildir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Çıktı `11 xyz`.

Bir `mutable` anahtar sözcüğü olmadan yapınızı `mutable` alanlarla başlatacaksanız, atamalarınız **, atamadan**sonra atılacak yapının bir kopyası üzerinde çalışacaktır. Bu nedenle, yapınız değişmeyecek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Açık alanlar, rutin kullanım için tasarlanmamıştır. Genel olarak, mümkün olduğunda açık bir alan yerine bir sınıfta `let` bağlama kullanmanız gerekir. Açık alanlar, yerel API 'ye yönelik platform çağırma çağrısında veya COM birlikte çalışma senaryolarında kullanılacak bir yapı tanımlamanız gerektiğinde olduğu gibi, belirli birlikte çalışabilirlik senaryolarında yararlıdır. Daha fazla bilgi için bkz. [dış işlevler](../functions/external-functions.md). Bir açık alanın gerekli olabileceği başka bir durum ise, sınıfları birincil Oluşturucu olmadan yayar bir F# kod Oluşturucu ile çalışmaktır. Açık alanlar, iş parçacığı statik değişkenleri veya benzer yapılar için de kullanışlıdır. Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.

Anahtar sözcükler `member val` bir tür tanımında birlikte görüntülendiğinde, otomatik olarak uygulanan bir özelliğin tanımıdır. Daha fazla bilgi için bkz. [Özellikler](properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](properties.md)
- [Üyeler](index.md)
- [Sınıflarda `let` bağlamaları](let-bindings-in-classes.md)
