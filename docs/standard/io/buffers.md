---
title: System. buffers-.NET
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
# <a name="work-with-buffers-in-net"></a>.NET 'teki arabelleklerle çalışma

Bu makalede, birden çok arabelleğe çalışan verileri okumaya yardımcı olan türlere genel bakış sunulmaktadır. Bunlar öncelikle nesneleri desteklemek için kullanılır <xref:System.IO.Pipelines.PipeReader> .

## <a name="ibufferwritert"></a>Ibufferwriter \< T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>, zaman uyumlu arabelleğe alınmış yazma için bir sözleşmedir. En düşük düzeyde, arabirimi:

- Temel ve kullanılması zor değildir.
- Veya erişimine izin verir <xref:System.Memory%601> <xref:System.Span%601> . `Memory<T>`Veya `Span<T>` üzerine yazılabilir ve kaç `T` öğe yazıldığını belirleyebilirsiniz.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Önceki Yöntem:

- Kullanarak en az 5 baytlık bir arabellek ister `IBufferWriter<byte>` `GetSpan(5)` .
- "Hello" ASCII dizesi için verilen baytları döndürülen öğesine yazar `Span<byte>` .
- <xref:System.Buffers.IBufferWriter%601>Arabelleğe kaç bayt yazıldığını belirten çağrılar.

Bu yazma yöntemi `Memory<T>` / `Span<T>` , tarafından sağlanmış olan arabelleği kullanır `IBufferWriter<T>` . Alternatif olarak, <xref:System.Buffers.BuffersExtensions.Write%2A> genişletme yöntemi var olan bir arabelleği öğesine kopyalamak için kullanılabilir `IBufferWriter<T>` . `Write`, doğru çağırma işini yapar `GetSpan` / `Advance` , bu nedenle `Advance` yazmadan sonra çağrı gerekmez:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>, `IBufferWriter<T>` yedekleme deposu tek bir bitişik dizi olan uygulamasıdır.

### <a name="ibufferwriter-common-problems"></a>Ibufferwriter yaygın sorunlar

- `GetSpan`ve `GetMemory` en az istenen bellek miktarına sahip bir arabellek döndürür. Tam arabellek boyutlarını kabul etmeyin.
- Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.
- `Advance`Daha fazla veri yazmaya devam etmek için çağrıldıktan sonra yeni bir arabellek istenmesi gerekir. Daha önce elde edilen bir arabellek çağrıldıktan sonra üzerine yazılamaz `Advance` .

## <a name="readonlysequencet"></a>ReadOnlySequence \< T\>

![Salt okunan belleğin sıra konumunun kanalda ve altında belleği gösteren ReadOnlySequence](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>, ardışık veya bitişik olmayan dizisini temsil eden bir struct `T` . Oluşturulabilir:

1. Bir `T[]`
1. Bir `ReadOnlyMemory<T>`
1. <xref:System.Buffers.ReadOnlySequenceSegment%601>Dizinin başlangıç ve bitiş konumunu temsil eden bağlantılı liste düğümü ve Dizin çifti.

Üçüncü Gösterim, üzerinde çeşitli işlemlerde performans etkilerine sahip olduğu için en ilginç bir gösterimidir `ReadOnlySequence<T>` :

|İmle|Çalışma|Karmaşıklık|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Bu karışık Gösterim nedeniyle `ReadOnlySequence<T>` dizinleri `SequencePosition` bir tamsayı yerine kullanıma sunar. Y `SequencePosition` :

- , Kaynaklandığı yere bir dizin temsil eden donuk bir değerdir `ReadOnlySequence<T>` .
- İki bölümden oluşur, bir tamsayı ve bir nesne. Bu iki değerin uygulamasının uygulamasına bağlı olması `ReadOnlySequence<T>` .

### <a name="access-data"></a>Verilere erişme

`ReadOnlySequence<T>`Verileri numaralandırılabilir olarak gösterir `ReadOnlyMemory<T>` . Parçaların her birini numaralandırma, temel bir foreach kullanılarak yapılabilir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Yukarıdaki yöntem, her segmenti belirli bir bayt arar. Her bir parçayı takip etmeniz gerekiyorsa `SequencePosition` , <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> daha uygundur. Sonraki örnek, önceki kodu bir tamsayı yerine döndürecek şekilde değiştirir `SequencePosition` . Bir döndürmek `SequencePosition` , çağıranın belirli bir dizindeki verileri almak için ikinci bir taramayı önlemenize izin vermenin avantajına sahiptir.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Birleşimi `SequencePosition` ve `TryGet` bir Numaralandırıcı gibi davranır. Konum alanı her bir yinelemenin başlangıcında, içindeki her bir segmentin başlaması için değiştirilir `ReadOnlySequence<T>` .

Önceki yöntem üzerinde bir genişletme yöntemi olarak mevcuttur `ReadOnlySequence<T>` . <xref:System.Buffers.BuffersExtensions.PositionOf%2A>, önceki kodu basitleştirmek için kullanılabilir:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>ReadOnlySequence T işleme \<\>

`ReadOnlySequence<T>`Verilerin dizideki birden çok parçaya bölünmesi gerektiğinden, işleme bir işlem zor olabilir. En iyi performansı elde etmek için kodu iki yola ayırın:

- Tek kesimli büyük/küçük harf ile ilgilenen hızlı bir yol.
- Bölümler arasında bölünen verilerle ilgilenen yavaş bir yol.

Verileri çok kesimli dizilerden işlemek için kullanılabilecek birkaç yaklaşım vardır:

- Kullanın [`SequenceReader<T>`](#sequencereadert) .
- Segmenti segmente göre ayrıştırır, `SequencePosition` kesim içindeki ve dizininin izini saklayın. Bu, gereksiz ayırmaları önler, ancak özellikle küçük arabellekler için verimsiz olabilir.
- Öğesini `ReadOnlySequence<T>` bitişik bir diziye kopyalayın ve tek bir arabellek gibi değerlendirin:
  - Boyutu `ReadOnlySequence<T>` küçükse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) işleci kullanılarak verileri yığına ayrılmış bir arabelleğe kopyalamanız makul olabilir.
  - Öğesini `ReadOnlySequence<T>` kullanarak havuza alınmış bir diziye kopyalayın <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> .
  - [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) adresini kullanın. Bu, yığın üzerinde yeni bir ayırdığı için etkin yollarda önerilmez `T[]` .

Aşağıdaki örneklerde, işleme için bazı yaygın durumlar gösterilmektedir `ReadOnlySequence<byte>` :

##### <a name="process-binary-data"></a>İkili verileri işle

Aşağıdaki örnek, öğesinin başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır `ReadOnlySequence<byte>` .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Metin verilerini işleme

Aşağıdaki örnek:

- İçindeki ilk yeni satırı ( `\r\n` ) bulur `ReadOnlySequence<byte>` ve ' Line ' parametresi aracılığıyla döndürür.
- Giriş arabelleğinden hariç bırakarak bu satırı kırpar `\r\n` .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Boş segmentler

Boş kesimleri bir içinde depolamak için geçerlidir `ReadOnlySequence<T>` . Kesimleri açıkça Numaralandırırken boş kesimler meydana gelebilir:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Yukarıdaki kod, `ReadOnlySequence<byte>` boş kesimleri olan bir oluşturur ve bu boş segmentlerin çeşitli API 'leri nasıl etkilediğini gösterir:

- `ReadOnlySequence<T>.Slice`boş bir `SequencePosition` kesime işaret eden, bu segmenti korur.
- `ReadOnlySequence<T>.Slice`bir int ile boş kesimleri atlar.
- Numaralandırma, `ReadOnlySequence<T>` boş kesimleri numaralandırır.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>ReadOnlySequence \< T> ve SequencePosition ile ilgili olası sorunlar

Bir ile ve normal arasında işlem yaparken birkaç olağandışı sonuç vardır `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` :

- `SequencePosition``ReadOnlySequence<T>`, mutlak bir konum değil, belirli bir konum işaretleyicisi. Belirli bir göreli olduğundan `ReadOnlySequence<T>` , kaynaklandığı konum dışında kullanılırsa anlamı yoktur `ReadOnlySequence<T>` .
- Aritmetik, olmadan üzerinde gerçekleştirilemez `SequencePosition` `ReadOnlySequence<T>` . Bu, gibi temel nesnelerin `position++` yazıldığı anlamına gelir `ReadOnlySequence<T>.GetPosition(position, 1)` .
- `GetPosition(long)`negatif **dizinleri desteklemez.** Diğer bir deyişle, tüm kesimleri yürümeden ikinciden son karaktere ulaşmak mümkün değildir.
- İkisi `SequencePosition` karşılaştırılamıyor, şunları yapmayı zorlaştırıyor:
  - Bir konumun başka bir konumdan büyük veya küçük olup olmadığını öğrenin.
  - Bazı ayrıştırma algoritmaları yazın.
- `ReadOnlySequence<T>`, bir nesne başvurusundan daha büyük ve [içinde](../../csharp/language-reference/keywords/in-parameter-modifier.md) ya da mümkün olduğunda [başvuru](../../csharp/language-reference/keywords/ref.md) olarak geçirilmelidir. `ReadOnlySequence<T>` `in` `ref` [Yapının](../../csharp/language-reference/builtin-types/struct.md)kopyalarını geçirerek veya azaltır.
- Boş segmentler:
  - , Bir içinde geçerlidir `ReadOnlySequence<T>` .
  - Yöntemi kullanılarak yinelenirken görünebilirler `ReadOnlySequence<T>.TryGet` .
  - , Metodu nesneleriyle birlikte kullanarak diziyi Dilimleme gibi görünebilir `ReadOnlySequence<T>.Slice()` `SequencePosition` .

## <a name="sequencereadert"></a>SequenceReader \< T\>

<xref:System.Buffers.SequenceReader%601>:

- , .NET Core 3,0 ' de tanıtılan ve işlemesini basitleştirecek yeni bir türdür `ReadOnlySequence<T>` .
- Tek bir segment `ReadOnlySequence<T>` ve çok segment arasındaki farkları birleştirir `ReadOnlySequence<T>` .
- `byte` `char` , Parçalar arasında bölünecek veya bölünemeyeceği ikili ve metin verilerini (ve) okumak için yardımcılar sağlar.

Hem ikili hem de sınırlandırılmış verilerin işlenmesiyle ilgili yerleşik yöntemler vardır. Aşağıdaki bölümde, aynı yöntemlerin bu şekilde nasıl gösterdiği gösterilmektedir `SequenceReader<T>` :

### <a name="access-data"></a>Verilere erişme

`SequenceReader<T>`, doğrudan içindeki verileri numaralandırma yöntemlerine sahiptir `ReadOnlySequence<T>` . Aşağıdaki kod, bir seferde bir işlem işleme örneğidir `ReadOnlySequence<byte>` `byte` :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

, `CurrentSpan` `Span` Yönteminde el ile yapılan yönteme benzer şekilde, geçerli segmenti kullanıma sunar.

### <a name="use-position"></a>Kullanım konumu

Aşağıdaki kod, şunu kullanmanın örnek bir uygulamasıdır `FindIndexOf` `SequenceReader<T>` :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>İkili verileri işle

Aşağıdaki örnek, öğesinin başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır `ReadOnlySequence<byte>` .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Metin verilerini işleme

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader \< T \> yaygın sorunlar

- `SequenceReader<T>`Değişebilir bir yapı olduğundan, her zaman [başvuruya](../../csharp/language-reference/keywords/ref.md)göre geçirilmelidir.
- `SequenceReader<T>`yalnızca zaman uyumlu metotlarda kullanılabilmesi ve alanlarda depolanabilmesi için [başvuru yapısı](../../csharp/language-reference/builtin-types/struct.md#ref-struct) . Daha fazla bilgi için bkz. [yazma güvenli ve verimli C# kodu](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>`yalnızca ileri bir okuyucu olarak kullanılmak üzere iyileştirilmiştir. `Rewind`, diğer `Read` , ve API 'lerden yararlanarak belirtilemeyilecek küçük yedeklemeler için tasarlanmıştır `Peek` `IsNext` .
