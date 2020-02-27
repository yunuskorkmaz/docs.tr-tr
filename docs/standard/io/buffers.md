---
title: System. buffers-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 5b98e3e2d41d3e49a28db6393f15f13c3579b06d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628084"
---
# <a name="work-with-buffers-in-net"></a>.NET 'teki arabelleklerle çalışma

Bu makalede, birden çok arabelleğe çalışan verileri okumaya yardımcı olan türlere genel bakış sunulmaktadır. Bunlar öncelikle <xref:System.IO.Pipelines.PipeReader> nesneleri desteklemek için kullanılır.

## <a name="ibufferwritert"></a>Ibufferwriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>, zaman uyumlu arabelleğe alınmış yazma için bir sözleşmedir. En düşük düzeyde, arabirimi:

- Temel ve kullanılması zor değildir.
- <xref:System.Memory%601> veya <xref:System.Span%601>erişimine izin verir. `Memory<T>` veya `Span<T>` üzerine yazılabilir ve kaç `T` öğe yazıldığını belirleyebilirsiniz.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Önceki Yöntem:

- `GetSpan(5)`kullanarak `IBufferWriter<byte>` en az 5 baytlık bir arabellek ister.
- "Hello" ASCII dizesi için döndürülen `Span<byte>`bayt yazar.
- Arabelleğe kaç bayt yazıldığını belirten <xref:System.Buffers.IBufferWriter%601> çağırır.

Bu yazma yöntemi, `IBufferWriter<T>`tarafından sunulan `Memory<T>`/`Span<T>` arabelleğini kullanır. Alternatif olarak, <xref:System.Buffers.BuffersExtensions.Write%2A> uzantısı yöntemi mevcut bir arabelleği `IBufferWriter<T>`kopyalamak için kullanılabilir. `Write`, `GetSpan`/`Advance` uygun şekilde çağırmada çalışır; bu nedenle, yazdıktan sonra `Advance` çağrısına gerek yoktur:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>, yedekleme deposu tek bir bitişik dizi olan `IBufferWriter<T>` uygulamasıdır.

### <a name="ibufferwriter-common-problems"></a>Ibufferwriter yaygın sorunlar

- `GetSpan` ve `GetMemory` en az istenen bellek miktarına sahip bir arabellek döndürür. Tam arabellek boyutlarını kabul etmeyin.
- Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.
- Daha fazla veri yazmaya devam etmek için `Advance` çağrıldıktan sonra yeni bir arabellek istenmesi gerekir. Daha önce elde edilen bir arabellek `Advance` çağrıldıktan sonra yazılamaz.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![Salt okunan belleğin sıra konumunun kanalda ve altında belleği gösteren ReadOnlySequence](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>, bitişik veya bitişik olmayan bir `T`dizisini temsil eden bir struct. Oluşturulabilir:

1. Bir `T[]`
1. Bir `ReadOnlyMemory<T>`
1. Dizinin başlangıç ve bitiş konumunu temsil etmek için bir çift bağlantılı liste düğümü <xref:System.Buffers.ReadOnlySequenceSegment%601> ve dizini.

Üçüncü Gösterim, `ReadOnlySequence<T>`çeşitli işlemlerde performans etkilerine sahip olduğu için en ilginç bir gösterimidir:

|İmle|İşlem|Karmaşıklık|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Bu karışık Gösterim nedeniyle `ReadOnlySequence<T>` dizinleri bir tamsayı yerine `SequencePosition` olarak kullanıma sunar. `SequencePosition`:

- , `ReadOnlySequence<T>` kaynaklandığı bir dizini temsil eden donuk bir değerdir.
- İki bölümden oluşur, bir tamsayı ve bir nesne. Bu iki değerin ne gösterdiği, `ReadOnlySequence<T>`uygulamasına bağlıdır.

### <a name="access-data"></a>Verilere erişme

`ReadOnlySequence<T>`, verileri sıralanabilir bir `ReadOnlyMemory<T>`olarak kullanıma sunar. Parçaların her birini numaralandırma, temel bir foreach kullanılarak yapılabilir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Yukarıdaki yöntem, her segmenti belirli bir bayt arar. Her bir segmentin `SequencePosition`izlemeniz gerekiyorsa <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> daha uygundur. Sonraki örnek, önceki kodu bir tamsayı yerine bir `SequencePosition` döndürecek şekilde değiştirir. `SequencePosition` döndürmek, çağıranın belirli bir dizindeki verileri almak için ikinci bir taramayı önlemenize izin vermenin avantajına sahiptir.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

`SequencePosition` ve `TryGet` birleşimi bir Numaralandırıcı gibi davranır. Konum alanı her bir yinelemenin başlangıcında, `ReadOnlySequence<T>`içindeki her bir segmentin başlaması için değiştirilir.

Önceki yöntem `ReadOnlySequence<T>`bir genişletme yöntemi olarak mevcuttur. <xref:System.Buffers.BuffersExtensions.PositionOf%2A>, önceki kodu basitleştirmek için kullanılabilir:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>ReadOnlySequence\<T\> işleme

Verilerin dizideki birden çok parçaya bölünmesi gerektiğinden, bir `ReadOnlySequence<T>` işleme zor olabilir. En iyi performansı elde etmek için kodu iki yola ayırın:

- Tek kesimli büyük/küçük harf ile ilgilenen hızlı bir yol.
- Bölümler arasında bölünen verilerle ilgilenen yavaş bir yol.

Verileri çok kesimli dizilerden işlemek için kullanılabilecek birkaç yaklaşım vardır:

- [`SequenceReader<T>`](#sequencereadert)kullanın.
- Segmenti segmente göre ayrıştırır, `SequencePosition` ve dizinin içindeki dizini ayrıştırın. Bu, gereksiz ayırmaları önler, ancak özellikle küçük arabellekler için verimsiz olabilir.
- `ReadOnlySequence<T>` bitişik bir diziye kopyalayın ve tek bir arabellek gibi değerlendirin:
  - `ReadOnlySequence<T>` boyutu küçükse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) işleci kullanılarak verileri yığına ayrılan bir arabelleğe kopyalamak makul olabilir.
  - <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>kullanarak `ReadOnlySequence<T>` havuza alınmış bir diziye kopyalayın.
  - [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) adresini kullanın. Bu, yığın üzerinde yeni bir `T[]` ayırdığı için etkin yollarda önerilmez.

Aşağıdaki örneklerde `ReadOnlySequence<byte>`işlemeye yönelik bazı genel durumlar gösterilmektedir:

##### <a name="process-binary-data"></a>İkili verileri işle

Aşağıdaki örnek, `ReadOnlySequence<byte>`başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Metin verilerini işleme

Aşağıdaki örnek:

- `ReadOnlySequence<byte>` ilk yeni satırı (`\r\n`) bulur ve out ' Line ' parametresi aracılığıyla döndürür.
- Giriş arabelleğindeki `\r\n` hariç bırakarak bu satırı kırpar.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Boş segmentler

Boş kesimleri bir `ReadOnlySequence<T>`içinde depolamak geçerlidir. Kesimleri açıkça Numaralandırırken boş kesimler meydana gelebilir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Yukarıdaki kod, boş kesimleri olan bir `ReadOnlySequence<byte>` oluşturur ve bu boş segmentlerin çeşitli API 'Leri nasıl etkilediğini gösterir:

- boş bir kesime işaret eden bir `SequencePosition` `ReadOnlySequence<T>.Slice`, bu segmenti korur.
- bir int ile `ReadOnlySequence<T>.Slice` boş kesimleri atlar.
- `ReadOnlySequence<T>` numaralandırılırken boş segmentler numaralandırılır.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>ReadOnlySequence\<T > ve SequencePosition ile ilgili olası sorunlar

Bir `ReadOnlySequence<T>`/ile ilgilenirken olağan dışı sonuçlar vardır `SequencePosition` vs `ReadOnlySpan<T>`. /`ReadOnlyMemory<T>`/`T[]`/`int`:

- `SequencePosition`, mutlak bir konum değil, belirli bir `ReadOnlySequence<T>`için konum işaretleyicisidir. Belirli bir `ReadOnlySequence<T>`göreli olduğundan, kaynaklandığı `ReadOnlySequence<T>` dışında kullanılırsa anlamı yoktur.
- Aritmetik, `ReadOnlySequence<T>`olmadan `SequencePosition` gerçekleştirilemez. Bu, `position++` gibi temel nesnelerin `ReadOnlySequence<T>.GetPosition(position, 1)`yazıldığı anlamına gelir.
- `GetPosition(long)` negatif **dizinleri desteklemez.** Diğer bir deyişle, tüm kesimleri yürümeden ikinciden son karaktere ulaşmak mümkün değildir.
- İki `SequencePosition` karşılaştırılamaz ve şunları yapmayı zorlaştırıyor:
  - Bir konumun başka bir konumdan büyük veya küçük olup olmadığını öğrenin.
  - Bazı ayrıştırma algoritmaları yazın.
- `ReadOnlySequence<T>` bir nesne başvurusundan daha büyük ve [içinde](../../csharp/language-reference/keywords/in-parameter-modifier.md) ya da mümkün olduğunda [başvuru](../../csharp/language-reference/keywords/ref.md) olarak geçirilmelidir. `in` veya `ref` tarafından `ReadOnlySequence<T>` geçirme [yapının](../../csharp/language-reference/builtin-types/struct.md)kopyalarını azaltır.
- Boş segmentler:
  - `ReadOnlySequence<T>`içinde geçerlidir.
  - `ReadOnlySequence<T>.TryGet` yöntemi kullanılarak yinelenirken görünebilirler.
  - `SequencePosition` nesneleri ile `ReadOnlySequence<T>.Slice()` yöntemi kullanılarak diziyi Dilimleme görünebilir.

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- , Bir `ReadOnlySequence<T>`işlenmesini basitleştirmek için .NET Core 3,0 ' de tanıtılan yeni bir türdür.
- Tek bir kesim `ReadOnlySequence<T>` ve çok kesimli `ReadOnlySequence<T>`arasındaki farkları birleştirir.
- Bölümler arasında bölünecek veya bölünmemiş olabilecek ikili ve metin verilerini (`byte` ve `char`) okumak için yardımcılar sağlar.

Hem ikili hem de sınırlandırılmış verilerin işlenmesiyle ilgili yerleşik yöntemler vardır. Aşağıdaki bölümde, bu yöntemlerin `SequenceReader<T>`nasıl göründüğünü gösterilmektedir:

### <a name="access-data"></a>Verilere erişme

`SequenceReader<T>`, `ReadOnlySequence<T>` içindeki verileri doğrudan numaralandırma yöntemlerine sahiptir. Aşağıdaki kod, bir `ReadOnlySequence<byte>` `byte` bir anda işleme örneğidir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

`CurrentSpan`, geçerli segmentin `Span`, yöntemde yapılan yönteme benzer şekilde kullanıma sunar.

### <a name="use-position"></a>Kullanım konumu

Aşağıdaki kod, `SequenceReader<T>`kullanarak `FindIndexOf` örnek bir uygulamasıdır:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>İkili verileri işle

Aşağıdaki örnek, `ReadOnlySequence<byte>`başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Metin verilerini işleme

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<T\> genel sorunlar

- `SequenceReader<T>` kesilebilir bir struct olduğundan, her zaman [başvuruya](../../csharp/language-reference/keywords/ref.md)göre geçirilmesi gerekir.
- `SequenceReader<T>`, yalnızca zaman uyumlu metotlarda kullanılabilmesi ve alanlarda depolanabilmesi için [başvuru yapısı](../../csharp/language-reference/keywords/ref.md#ref-struct-types) . Daha fazla bilgi için bkz. [yazma güvenli ve C# verimli kod](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>` yalnızca ileri bir okuyucu olarak kullanılmak üzere iyileştirilmiştir. `Rewind`, diğer `Read`, `Peek`ve `IsNext` API 'Lerini kullanarak değinilmemiş küçük yedeklemeler için tasarlanmıştır.
