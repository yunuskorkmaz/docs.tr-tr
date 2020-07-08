---
title: Anonim ve demet türleri arasında seçim yapma
description: Anonim türler ve demet türü arasında seçim yapmak için uygun olduğunda bilgi edinin.
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 2f927b59d7206dd0f405c11529f93b56a1c778a0
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052084"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>Anonim ve demet türleri arasında seçim yapma

Uygun türü seçmek, diğer türlere kıyasla kullanılabilirlik, performans ve dengelenmesini kapsar. Anonim türler C# 3,0 ' den beri kullanılabilir, ancak genel <xref:System.Tuple%602?displayProperty=nameWithType> türler .NET Framework 4,0 ile tanıtılmıştır. Daha sonra, adın gösterdiği gibi dil düzeyi desteğiyle yeni seçenekler tanıtıldığından, <xref:System.ValueTuple%602?displayProperty=nameWithType> anonim türlerin esnekliğine sahip bir değer türü sağlayın. Bu makalede, diğer bir tür seçmek için uygun olduğunda öğrenirsiniz.

## <a name="usability-and-functionality"></a>Kullanılabilirlik ve işlevsellik

Anonim türler, dil ile tümleşik sorgu (LINQ) ifadeleriyle C# 3,0 ' de tanıtılmıştır. LINQ ile, geliştiriciler genellikle sorguları üzerinde çalıştıkları nesnelerden birkaç Select özelliği tutan anonim türlere göre proje sonuçları. Aşağıdaki örneği bir nesne dizisi örnekleyen <xref:System.DateTime> ve iki özelliği olan anonim bir türde bir şekilde taşıyan bir değer ile yineleyen bir değer düşünün.

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

Anonim türler işleç kullanılarak örneklenmiştir [`new`](../../csharp/language-reference/operators/new-operator.md) ve özellik adları ve türleri bildirimden algılanır. Aynı derlemede bulunan iki veya daha fazla anonim nesne başlatıcıları aynı sırada olan ve aynı ada ve türe sahip olan bir özellikler sırası belirtse, derleyici nesneleri aynı türdeki örnekler olarak değerlendirir. Derleyici tarafından oluşturulan tür bilgilerini paylaşır.

Önceki C# kod parçacığı, aşağıdaki derleyici tarafından oluşturulan C# sınıfına benzer şekilde, iki özelliği olan anonim bir tür:

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

Daha fazla bilgi için bkz. [anonim türler](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). Aynı işlevsellik, LINQ sorgularında yansıtıladığında diziler halinde mevcuttur, Özellikler ' i tanımlama grupları ' na seçebilirsiniz. Bu tanımlama grupları, anonim türler gibi sorgu üzerinden akar. Şimdi, kullanarak aşağıdaki örneği göz önünde bulundurun `System.Tuple<string, long>` .

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

İle, <xref:System.Tuple%602?displayProperty=nameWithType> örneği, ve gibi numaralandırılmış öğe özelliklerini kullanıma sunar `Item1` `Item2` . Özellik adı yalnızca sıra sayısını sağladığından, bu özellik adları özellik değerlerinin amacını anlamak daha zor hale gelir. Ayrıca, `System.Tuple` türler başvuru `class` türleridir. <xref:System.ValueTuple%602?displayProperty=nameWithType>Ancak, bir değer `struct` türüdür. Aşağıdaki C# kod parçacığı, `ValueTuple<string, long>` içinde Project için kullanır. Bunu yaparken, değişmez bir sözdizimi kullanarak atar.

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

C#, türü ve anlamları olan tanımlama grupları için dil desteği sağlar <xref:System.ValueTuple> :

- [Demet atama](../../csharp/tuples.md#assignment-and-tuples)
- [Demet oluşturma](../../csharp/deconstruct.md) (tanımlama grupları ile sınırlı değil)
- [Tanımlama grubu eşitlik denetimleri](../../csharp/tuples.md#equality-and-tuples)
- [Demet projeksiyon başlatıcıları](../../csharp/tuples.md#tuple-projection-initializers)

Önceki örneklerin hepsi işlevsel olarak eşdeğerdir; ancak kullanılabilirlik ve temel uygulamalarında hafif farklar vardır.

## <a name="tradeoffs"></a>Avantajlar ve Dezavantajlar

Her zaman <xref:System.ValueTuple> <xref:System.Tuple> ve anonim türleri kullanmak isteyebilirsiniz, ancak göz önünde bulundurmanız gereken bir denge vardır. <xref:System.ValueTuple>Türler değişebilir, ancak <xref:System.Tuple> salt okunurdur. Anonim türler ifade ağaçlarında kullanılabilir, ancak diziler yapılamaz. Aşağıdaki tabloda bazı önemli farklılıklara ilişkin bir genel bakış sunulmaktadır.

### <a name="key-differences"></a>Temel farklılıklar

| Name                     | Erişim değiştiricisi | Tür     | Özel üye adı | Oluşturmayı kaldırma desteği | İfade ağacı desteği |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| Anonim türler          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>Serileştirme

Bir tür seçerken dikkat etmeniz gereken önemli bir nokta, serileştirilmesi gerekip gerekmediğini belirtir. Serileştirme, bir nesnenin durumunu kalıcı veya taşınan bir biçime dönüştürme işlemidir. Daha fazla bilgi için bkz. [serileştirme](../../csharp/programming-guide/concepts/serialization/index.md). Serileştirme önemli olduğunda, `class` `struct` anonim türler veya demet türleri üzerinde bir veya oluşturmak tercih edilir.

## <a name="performance"></a>Performans

Bu türler arasındaki performans senaryoya bağlıdır. Ana etki, ayırma ve kopyalama arasındaki zorunluluğunu getirir içerir. Çoğu senaryoda, etki küçüktür. Büyük etkileri ortaya çıktığında, kararı bildirmek için ölçümler gerçekleştirilmelidir.

## <a name="conclusion"></a>Sonuç

Bir geliştirici olarak tanımlama grupları ve anonim türler arasında seçim yaparak göz önünde bulundurmanız gereken birkaç etken vardır. Genellikle, [ifade ağaçları](../../csharp/expression-trees.md)ile çalışmadıysanız ve demet söz dizimine rahat bir şekilde sahip olduğunuzda, <xref:System.ValueTuple> özellik adı esnekliği ile bir değer türü sağlayan öğesini seçin. İfade ağaçları ile çalışıyorsanız ve özellikleri adlandırmak isterseniz, anonim türler ' i seçin. Aksi takdirde, kullanın <xref:System.Tuple> .

## <a name="see-also"></a>Ayrıca bkz.

- [Anonim türler](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [İfade ağaçları](../../csharp/expression-trees.md)
- [Demet türleri](../../csharp/tuples.md)
- [Tür tasarımı yönergeleri](../design-guidelines/type.md)
