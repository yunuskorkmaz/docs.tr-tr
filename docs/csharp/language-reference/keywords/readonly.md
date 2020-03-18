---
title: readonly anahtar kelime - C# Başvuru
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 165b6287e1610e013b289601e1535a08fdd3b5c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399359"
---
# <a name="readonly-c-reference"></a>readonly (C# Başvurusu)

Anahtar `readonly` kelime, dört bağlamda kullanılabilen bir değiştiricidir:

- Alan [bildiriminde,](#readonly-field-example) `readonly` alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda gerçekleşebileceğini belirtir. Yalnızca okunan bir alan, alan bildirimi ve oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir.
  
  Bir `readonly` alan, yapıcı çıktıktan sonra atanamaz. Bu kuralın değer türleri ve başvuru türleri için farklı etkileri vardır:
  
  - Değer türleri doğrudan verilerini içerdiğinden, değer `readonly` türü olan bir alan değişmez.
  - Başvuru türleri verilerine bir başvuru içerdiğinden, `readonly` başvuru türü olan bir alanın her zaman aynı nesneye başvurması gerekir. Bu nesne değişmez değil. Değiştirici, `readonly` alanın başvuru türünün farklı bir örneğiyle değiştirilmesini önler. Ancak, değiştirici, alanın örnek verilerinin salt okunur alanı boyunca değiştirilmesini engellemez.

  > [!WARNING]
  > Mutable başvuru türü olan harici olarak görünür salt okunur alan içeren harici olarak görünen bir tür bir güvenlik açığı olabilir ve [ca2104](/visualstudio/code-quality/ca2104) uyarısını tetikleyebilir: "Yalnızca mutable başvuru türlerini okumayı bildirin."

- Bir [ `readonly struct` tanımda,](#readonly-struct-example) `readonly` değişmez `struct` olduğunu gösterir.
- [ `readonly` Üye](#readonly-member-examples)tanımında, `readonly` bir `struct` üyenin yapının iç durumunu mutasyona uğratmadığını belirtir.
- Yöntem [ `ref readonly` dönüşünde,](#ref-readonly-return-example) `readonly` değiştirici yöntemin bir başvurudöndürür ve bu başvuru için yazı izin verilmez gösterir.

Ve `readonly struct` `ref readonly` bağlamlar C# 7.2'ye eklendi. `readonly`yapı üyeleri C# 8.0'a eklendi

## <a name="readonly-field-example"></a>Readonly alan örneği

Bu örnekte, sınıf oluşturucuya bir değer atanmış `ChangeYear`olsa bile, yöntemde alanın `year` değeri değiştirilemez:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Bir `readonly` alana yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:

- Değişken bildirimde başharfe geçtiğinde, örneğin:

  ```csharp
  public readonly int y = 5;
  ```

- Örnek alan bildirimini içeren sınıfın bir örnek oluşturucu.
- Statik alan bildirimini içeren sınıfın statik oluşturucuda.

Bu oluşturucu bağlamlar, bir `readonly` alanı dış [veya](out-parameter-modifier.md) [ref](ref.md) parametresi olarak geçirmenin geçerli olduğu tek bağlamdır.

> [!NOTE]
> Anahtar `readonly` kelime [const](const.md) anahtar kelime farklıdır. Bir `const` alan yalnızca alanın bildiriminde başlatılabilir. Alan `readonly` bildiriminde ve herhangi bir oluşturucuya birden çok kez atanabilir. Bu `readonly` nedenle, alanların kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir. Ayrıca, bir `const` alan derleme zamanı sabiti `readonly` olsa da, alan aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

Önceki örnekte, aşağıdaki örnek gibi bir deyim kullanırsanız:

```csharp
p2.y = 66;        // Error
```

derleyici hata iletisini alırsınız:

**Yalnızca okunan bir alan atanamıyor (bir oluşturucu veya değişken baş harfi hariç)**

## <a name="readonly-struct-example"></a>Readonly struct örnek

Tanımdaki `readonly` `struct` değiştirici, yapının **değişmez**olduğunu bildirir. Aşağıdaki örnekte `struct` gösterildiği gibi, her örnek alanı işaretlenmelidir: `readonly`

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

Önceki örnek, depolama alanını bildirmek için [salt okunur otomatik özelliklerini](../../properties.md#read-only) kullanır. Bu, derleyiciye bu `readonly` özellikler için destek alanları oluşturmasını bildirir. Alanları doğrudan `readonly` bildirebilirsiniz:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

İşaretlenmemiş `readonly` bir alan eklemek derleyici hatası `CS8340`oluşturur: "Yalnızca okunan yapıların örnek alanları yalnızca okunmalıdır."

## <a name="readonly-member-examples"></a>Readonly üye örnekleri

Diğer zamanlarda, mutasyonu destekleyen bir yapı oluşturabilirsiniz. Bu gibi durumlarda, örnek üyelerden bazıları büyük olasılıkla yapının iç durumunu değiştirmez. Bu örnek üyeleri `readonly` değiştirici ile bildirebilirsiniz. Derleyici niyetinizi zorlar. Bu üye durumu doğrudan değiştirirse veya `readonly` değiştiriciile birlikte bildirilmemiş bir üyeye erişirse, sonuç derleme zamanı hatasıdır. Değiştirici üyeler `struct` için geçerlidir, `class` `interface` üye beyannamelerinde veya üye beyanlarında geçerli değildir. `readonly`

`readonly` Değiştiriciyi geçerli `struct` yöntemlere uygulayarak iki avantaj elde elabilirsiniz. En önemlisi, derleyici niyetinizi zorlar. Durumu değiştiren kod bir `readonly` yöntemde geçerli değildir. Derleyici, performans optimizasyonlarını `readonly` etkinleştirmek için değiştiriciden de yararlanabilir. Büyük `struct` türler başvuru `in` yla geçirildiğinde, yapının durumu değiştirilse derleyicinin bir savunma kopyası oluşturması gerekir. Yalnızca `readonly` üyelere erişilirse, derleyici savunma kopyasını oluşturamaz.

`readonly` Değiştirici, 'de <xref:System.Object?displayProperty=nameWithType>bildirilen yöntemleri geçersiz kılma yöntemleri de dahil olmak üzere, bir `struct`üyenin çoğu üzerinde geçerlidir. Bazı kısıtlamalar vardır:

- Statik yöntemleri veya `readonly` özellikleri bildiremezsiniz.
- Yapıcıları beyan `readonly` edemezsin.

`readonly` Değiştiriciyi bir özellik veya dizinleyici bildirimine ekleyebilirsiniz:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

`readonly` Değiştiriciyi bir özellik veya `get` dizinleyicinin tek tek veya `set` erişimine de ekleyebilirsiniz:

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

`readonly` Değiştiriciyi hem bir özelliğe hem de aynı özelliğin erişimine bir veya daha fazla sınayabilirsiniz. Aynı kısıtlama dizinleyiciler için de geçerlidir.

Derleyici, derleyicinin `readonly` uygulanan kodun durumu değiştirmediği otomatik olarak uygulanan özelliklere dolaylı olarak değiştirici uygular. Aşağıdaki beyanlara eşdeğerdir:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

Bu konumlara `readonly` değiştirici ekleyebilirsiniz, ancak anlamlı bir etkisi olmayacaktır. `readonly` Değiştiriciyi otomatik olarak uygulanan bir özellik ayarlayıcısına veya otomatik olarak uygulanan bir özelliği okuma/yazma özelliğine ekleyebilirsiniz.

## <a name="ref-readonly-return-example"></a>Ref readonly dönüş örneği

A'daki `readonly` değiştirici, döndürülen başvurunun değiştirilemediğini `ref return` gösterir. Aşağıdaki örnek, kaynağına bir başvuru döndürür. Arayanların `readonly` kaynağı değiştiremediğini belirtmek için değiştirici kullanır:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Döndürülen tür bir `readonly struct`. olması gerekmez Tarafından `ref` döndürülebilen herhangi bir tür `ref readonly`.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Ayrıca dil belirtimi önerilerini de görebilirsiniz:

- [readonly ref ve readonly struct](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [readonly struct üyeleri](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Değiştiriciler](index.md)
- [const](const.md)
- [Alanlar](../../programming-guide/classes-and-structs/fields.md)
