---
title: System.Buffers - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739615"
---
# <a name="work-with-buffers-in-net"></a>.NET'te Arabelleklerle Çalışın

Bu makalede, birden çok arabellek te çalışan verilerin okunmasına yardımcı olan türlerin genel bir bakış sağlar. Öncelikle nesneleri desteklemek <xref:System.IO.Pipelines.PipeReader> için kullanılırlar.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>senkron arabellekli yazı için bir sözleşmedir. En düşük düzeyde, arabirim:

- Temel ve kullanımı zor değildir.
- Bir <xref:System.Memory%601> veya <xref:System.Span%601>. Veya `Memory<T>` `Span<T>` yazılabilir ve kaç `T` öğe nin yazıldığını belirleyebilirsiniz.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Önceki yöntem:

- `IBufferWriter<byte>` Kullanarak `GetSpan(5)`en az 5 bayt lık bir arabellek ister.
- Döndürülen `Span<byte>`ASCII dizesi "Hello" için bayt yazar.
- Arabelleğe kaç bayt yazıldığını gösteren çağrılar. <xref:System.Buffers.IBufferWriter%601>

Bu `Memory<T>` / `Span<T>` yazma yöntemi, `IBufferWriter<T>`.. Alternatif olarak, <xref:System.Buffers.BuffersExtensions.Write%2A> uzantı yöntemi varolan bir arabelleği kopyalamak için `IBufferWriter<T>`kullanılabilir. `Write`uygun olarak arama `GetSpan` / `Advance` işi yapar, bu nedenle yazdıktan sonra aramaya `Advance` gerek yoktur:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>`IBufferWriter<T>` olan destek deposu tek bir bitişik dizi bir uygulamadır.

### <a name="ibufferwriter-common-problems"></a>IBufferWriter sık karşılaşılan sorunlar

- `GetSpan`ve `GetMemory` en az istenen bellek miktarı ile bir arabellek döndürün. Tam arabellek boyutları varsayma.
- Ardışık aramaların aynı arabelleği veya aynı boyuttaara bellek döndüreceğinin garantisi yoktur.
- Daha fazla veri yazmaya devam `Advance` etmek için çağrıda bulunduktan sonra yeni bir arabellek istenmelidir. Daha önce edinilen bir arabellek `Advance` sonra çağrılmıştır yazılamaz.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence, belleği pipe'de ve salt okunur belleğin sıra konumunun altında gösteren](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>'nin bitişik veya bitişik olmayan sırasını temsil eden bir `T`yapıdır. Bu inşa edilebilir:

1. Bir `T[]`
1. Bir `ReadOnlyMemory<T>`
1. Dizinin başlangıç <xref:System.Buffers.ReadOnlySequenceSegment%601> ve bitiş konumunu temsil eden bağlantılı liste düğümü ve dizin çifti.

Üçüncü temsil en ilginç olan ın üzerinde çeşitli operasyonlar üzerinde `ReadOnlySequence<T>`performans etkileri vardır:

|Gösterimi|İşlem|Karmaşıklık|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Bu karışık gösterim nedeniyle, dizinleri `SequencePosition` tamsayı yerine ortaya `ReadOnlySequence<T>` çıkarır. A `SequencePosition`:

- Geldiği `ReadOnlySequence<T>` yere bir dizin temsil eden opak bir değerdir.
- İki bölümden oluşur, bir sasayı ve bir nesne. Bu iki değerin temsil iå `ReadOnlySequence<T>`lemi nin uygulanmasına bağlı olanı

### <a name="access-data"></a>Verilere erişme

Verileri `ReadOnlySequence<T>` bir yılbme olarak ortaya `ReadOnlyMemory<T>`çıkarır. Segmentlerin her biri sayısallama temel bir foreach kullanılarak yapılabilir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Önceki yöntem, her kesimi belirli bir bayt için arar. Her segmentin takip etmek `SequencePosition`gerekiyorsa, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> daha uygundur. Sonraki örnek, bir tamsayı yerine `SequencePosition` bir döndürmek için önceki kodu değiştirir. A'yı `SequencePosition` döndürme, arayanın belirli bir dizindeki verileri almak için ikinci bir tazından kaçınmasına izin verme avantajına sahiptir.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Kombinasyonu `SequencePosition` ve `TryGet` bir sayısalatör gibi davranır. Konum alanı, her yinelemenin başında, `ReadOnlySequence<T>`içindeki her kesimin başlangıcı olarak değiştirilir.

Önceki yöntem üzerinde `ReadOnlySequence<T>`bir uzantı yöntemi olarak var. <xref:System.Buffers.BuffersExtensions.PositionOf%2A>önceki kodu basitleştirmek için kullanılabilir:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Bir ReadOnlySequence\<T'yi İşleme\>

Veriler `ReadOnlySequence<T>` dizi içinde birden çok segmente bölünebildiği için a'yı işlemek zor olabilir. En iyi performans için kodu iki eşite bölün:

- Tek segmentli durumla ilgilenen hızlı bir yol.
- Segmentler arasında bölünmüş verilerle ilgilenen yavaş bir yol.

Verileri çok parçalı dizilerde işlemek için kullanılabilecek birkaç yaklaşım vardır:

- [`SequenceReader<T>`](#sequencereadert)Kullanın.
- Ayrışdırılmış segment içindeki `SequencePosition` ve dizin izleme, segmente göre ayrışt. Bu gereksiz ayırmaları önler, ancak özellikle küçük arabellekler için verimsiz olabilir.
- Bitişik `ReadOnlySequence<T>` bir diziye kopyalayın ve tek bir arabellek gibi davranın:
  - Boyutu `ReadOnlySequence<T>` küçükse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) işleci kullanarak verileri yığınayrılmış bir arabelleğe kopyalamak makul olabilir.
  - Kullanarak `ReadOnlySequence<T>` birleştirilmiş diziye <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>kopyalayın.
  - [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) adresini kullanın. Bu yığın üzerinde yeni `T[]` bir ayırır gibi sıcak yollarda tavsiye edilmez.

Aşağıdaki örnekler, işleme `ReadOnlySequence<byte>`için bazı yaygın durumlarda göstermektedir:

##### <a name="process-binary-data"></a>İkili verileri işleme

Aşağıdaki örnek, 4 baytlık bir büyük endian tamsayı uzunluğunu `ReadOnlySequence<byte>`başından itibaren ayrışdırır.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Metin verilerini işleme

Aşağıdaki örnek:

- İlk yeni hattı`\r\n`bulur ( `ReadOnlySequence<byte>` ) ve çıkış 'çizgi' parametresi ile döndürür.
- Giriş arabelleği `\r\n` hariç, bu satırı kırpar.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Boş segmentler

Boş segmentleri bir `ReadOnlySequence<T>`. Boş segmentler, segmentleri açıkça sayısalarken oluşabilir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Önceki kod boş segmentleri ile bir `ReadOnlySequence<byte>` oluşturur ve bu boş segmentleri çeşitli API'ler nasıl etkilediğini gösterir:

- `ReadOnlySequence<T>.Slice`boş `SequencePosition` bir segmente işaret ile bu kesimi korur.
- `ReadOnlySequence<T>.Slice`boş segmentler üzerinden atlar bir int ile.
- Boş segmentleri `ReadOnlySequence<T>` sayısallaştırıyor.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>ReadOnlySequence\<T> ve SequencePosition ile olası sorunlar

`ReadOnlySequence<T>` / Bir `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>`vs /normal `T[]`ile uğraşırken birkaç olağandışı sonuçları vardır: / `int`

- `SequencePosition`belirli `ReadOnlySequence<T>`bir pozisyon için bir konum işaretçisi, mutlak bir konum değil. Belirli bir göreceli olduğu `ReadOnlySequence<T>`için, geldiği `ReadOnlySequence<T>` yerin dışında kullanıldığında bir anlamı yoktur.
- Aritmetik `SequencePosition` olmadan `ReadOnlySequence<T>`yapılamaz. Bu, yazıldığı `ReadOnlySequence<T>.GetPosition(position, 1)`gibi `position++` temel şeyler yapmak anlamına gelir.
- `GetPosition(long)`negatif dizinleri **desteklemez.** Bu da demek oluyor ki, tüm bölümlerde yürümeden ikinciden son karaktere ulaşmak imkansız.
- İki `SequencePosition` karşılaştırılamaz, bu da zorlaştırır:
  - Bir konumun başka bir konumdan daha büyük mü yoksa daha az mı olduğunu bilin.
  - Bazı ayrışma algoritmaları yazın.
- `ReadOnlySequence<T>`bir nesne referansından daha büyüktür ve mümkünse içinde [veya](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../csharp/language-reference/keywords/ref.md) tarafından geçirilmelidir. Geçen `ReadOnlySequence<T>` `in` veya `ref` [yapıkopyalarını](../../csharp/language-reference/builtin-types/struct.md)azaltır.
- Boş segmentler:
  - Bir `ReadOnlySequence<T>`içinde geçerlidir.
  - `ReadOnlySequence<T>.TryGet` Yöntemi kullanarak yinelediğinde görünebilir.
  - Nesnelerle `ReadOnlySequence<T>.Slice()` `SequencePosition` yöntemi kullanarak dizi dilimleme görünebilir.

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- .NET Core 3.0'da bir işlemin basitleştirilmesini kolaylaştırmak `ReadOnlySequence<T>`için tanıtılan yeni bir türdür.
- Tek bir segment `ReadOnlySequence<T>` ve çok segment `ReadOnlySequence<T>`arasındaki farkları birleşdirir.
- Bölümlere bölünebilen veya bölünmeyen ikili ve metin verilerini (ve)`byte` `char`okumak için yardımcı sağlar.

Hem ikili hem de sınırlı verilerin işlenmesiyle başa çıkmak için yerleşik yöntemler vardır. Aşağıdaki bölümde bu aynı yöntemlerin `SequenceReader<T>`nasıl göründüğünü göstermektedir:

### <a name="access-data"></a>Verilere erişme

`SequenceReader<T>``ReadOnlySequence<T>` doğrudan içinde veri sayısallama yöntemleri vardır. Aşağıdaki kod, bir defada `ReadOnlySequence<byte>` `byte` a işleme örneğidir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

Geçerli `CurrentSpan` segmentin `Span`, yöntemde el ile yapılana benzer bir şekilde ortaya çıkarır.

### <a name="use-position"></a>Pozisyon kullanın

Aşağıdaki kod `FindIndexOf` kullanarak bir örnek `SequenceReader<T>`uygulamadır:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>İkili verileri işleme

Aşağıdaki örnek, 4 baytlık bir büyük endian tamsayı uzunluğunu `ReadOnlySequence<byte>`başından itibaren ayrışdırır.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Metin verilerini işleme

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<\> T sık karşılaşılan sorunlar

- Mutable bir yapı `SequenceReader<T>` olduğundan, her zaman [başvuru](../../csharp/language-reference/keywords/ref.md)ile geçirilmelidir.
- `SequenceReader<T>`bir [ref struct'dur,](../../csharp/language-reference/builtin-types/struct.md#ref-struct) bu nedenle yalnızca senkron yöntemlerle kullanılabilir ve alanlarda depolanamamaktadır. Daha fazla bilgi için bkz: [Güvenli ve verimli C# kodu yaz.](../../csharp/write-safe-efficient-code.md)
- `SequenceReader<T>`yalnızca ileri okuyucu olarak kullanılmak üzere optimize edilsin. `Rewind`diğer `Read`ve `Peek` `IsNext` API'ler kullanılarak ele alınamaz küçük yedeklemeler için tasarlanmıştır.
