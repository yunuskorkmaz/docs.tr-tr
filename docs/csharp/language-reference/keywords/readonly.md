---
title: ReadOnly anahtar sözcüğü C# -başvuru
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 8ecf399e48da12a9dee19bb217b8668c6a53d3ad
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191862"
---
# <a name="readonly-c-reference"></a>readonly (C# Başvurusu)

`readonly` anahtar sözcüğü dört bağlamda kullanılabilecek bir değiştiricisidir:

- [Alan bildiriminde](#readonly-field-example)`readonly`, alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda kullanılabileceğini gösterir. Salt okunur bir alan, alan bildirimi ve Oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir. 
  
  Oluşturucu çıktıktan sonra bir `readonly` alanı atanamaz. Bu kural, değer türleri ve başvuru türleri için farklı etkilere sahiptir:
  
  - Değer türleri doğrudan verilerini içerdiğinden, `readonly` değer türü olan bir alan sabittir. 
  - Başvuru türleri, verilerine yönelik bir başvuru içerdiğinden, `readonly` başvuru türü olan bir alan her zaman aynı nesneye başvurmalıdır. Bu nesne sabit değildir. `readonly` değiştiricisi, alanın farklı bir başvuru türü örneğiyle değiştirilmesini önler. Ancak, değiştirici alanın örnek verilerinin salt okunurdur alanı aracılığıyla değiştirilmesini engellemez.

  > [!WARNING]
  > Değişebilir bir başvuru türü olan bir dışarıdan görünür salt okunurdur alanı içeren dışarıdan görünen bir tür, bir güvenlik açığı olabilir ve uyarı [CA2104](/visualstudio/code-quality/ca2104) : "salt okuma kesilebilir başvuru türleri bildiremiyor" olarak tetiklenebilir.

- [`readonly struct` tanımında](#readonly-struct-example), `readonly` `struct` sabit olduğunu gösterir.
- [`readonly` üye tanımında](#readonly-member-examples), `readonly` bir `struct` üyesinin yapının iç durumunu muiçermediğini belirtir.
- `ref readonly` bir [yöntemde döndürülen](#ref-readonly-return-example)`readonly` değiştirici, yöntemin bir başvuru döndürdüğünü ve bu başvuruya yazma izni bulunmadığını gösterir.

`readonly sturct` ve `ref readonly` bağlamları 7,2 ' C# ye eklenmiştir. 8,0 ' de C# `readonly` struct üyeleri eklendi

## <a name="readonly-field-example"></a>ReadOnly alan örneği

Bu örnekte, `year` alan değeri, sınıf oluşturucusunda bir değer atanmış olsa da, `ChangeYear`yönteminde değiştirilemez:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Bir `readonly` alanına yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:

- Bildirimde bir değişken başlatıldığında, örneğin:

  ```csharp
  public readonly int y = 5;
  ```

- Örnek alan bildirimini içeren sınıfın örnek oluşturucusunda.
- Statik alan bildirimini içeren sınıfın statik oluşturucusunda.

Bu Oluşturucu bağlamları aynı zamanda bir `readonly` alanını [Out](out-parameter-modifier.md) veya [ref](ref.md) parametresi olarak geçirmek için geçerli olduğu tek bağlamlardır.

> [!NOTE]
> `readonly` anahtar sözcüğü [const](const.md) anahtar sözcüğünden farklıdır. Bir `const` alanı yalnızca alanın bildiriminde başlatılabilir. `readonly` alan, alan bildiriminde ve herhangi bir oluşturucuda birden çok kez atanabilir. Bu nedenle, `readonly` alanlar kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir. Ayrıca, bir `const` alanı bir derleme zamanı sabiti olsa da, `readonly` alanı aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

Yukarıdaki örnekte, aşağıdaki örnekte olduğu gibi bir ifade kullanıyorsanız:

```csharp
p2.y = 66;        // Error
```

Derleyici hata iletisini alırsınız:

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a>ReadOnly struct örneği

`struct` tanımında `readonly` değiştiricisi yapının **sabit**olduğunu bildirir. Aşağıdaki örnekte gösterildiği gibi `struct` her örnek alanı `readonly`işaretlenmelidir:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

Önceki örnek, depolama alanını bildirmek için [salt okunur otomatik özellikleri](../../properties.md#read-only) kullanır. Bu, derleyiciye bu özellikler için `readonly` yedekleme alanı oluşturmasını söyler. Ayrıca, `readonly` alanları doğrudan de bildirebilirsiniz:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

`readonly` işaretlenmemiş bir alan eklendiğinde `CS8340`derleyici hatası oluşturulur: "ReadOnly yapıların örnek alanları ReadOnly olmalıdır."

## <a name="readonly-member-examples"></a>ReadOnly üye örnekleri

Diğer zamanlarda, mutasyonu destekleyen bir yapı oluşturabilirsiniz. Bu durumlarda, örnek üyelerinden birkaçı büyük olasılıkla yapının iç durumunu değiştirmez. Bu örnek üyelerini `readonly` değiştiricisiyle bildirebilirsiniz. Derleyici amacınızı zorluyor. Bu üye, durumu doğrudan değiştirir veya `readonly` değiştiricisi ile de bildirilmeyen bir üyeye eriştiğinde sonuç, derleme zamanı hatasıdır. `readonly` değiştiricisi `class` veya `interface` üye bildirimlerinde değil `struct` üyelerinde geçerlidir.

Geçerli `struct` yöntemlerine `readonly` değiştiricisini uygulayarak iki avantaja sahip olursunuz. En önemlisi, derleyici amacınızı zorluyor. Durumu değiştiren kod `readonly` yönteminde geçerli değildir. Derleyici, performans iyileştirmelerini etkinleştirmek için `readonly` değiştiricisinden da kullanabilir. Büyük `struct` türleri `in` başvurusuyla geçirildiğinde, yapının durumu değiştirilemiyorsa derleyicinin bir savunma kopyası oluşturması gerekir. Yalnızca `readonly` üyelerine erişilirse, derleyici savunma kopyasını oluşturmayabilir.

`readonly` değiştiricisi, <xref:System.Object?displayProperty=nameWithType>tarafından belirtilen yöntemleri geçersiz kılan yöntemler de dahil olmak üzere `struct`çoğu üye üzerinde geçerlidir. Bazı kısıtlamalar vardır:

- `readonly` statik üye bildiremezsiniz.
- `readonly` oluşturucuları bildiremezsiniz.

`readonly` değiştiricisini bir özellik veya Dizin Oluşturucu bildirimine ekleyebilirsiniz:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

`readonly` değiştiricisini bir özelliğin veya dizin oluşturucunun tek tek `get` veya `set` erişimcilerine de ekleyebilirsiniz:

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

`readonly` değiştiricisini hem özelliğe hem de aynı özelliğin erişimcilerine bir veya daha fazlasına ekleyemeyebilirsiniz. Aynı kısıtlama, Dizin oluşturucular için geçerlidir.

Derleyici, derleyicinin uyguladığı kodun durumu değiştirmediğinden otomatik uygulanan özelliklere `readonly` değiştiricisini örtülü olarak uygular. Aşağıdaki bildirimlerle eşdeğerdir:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

`readonly` değiştiricisini bu konumlara ekleyebilirsiniz, ancak anlamlı bir etkiye sahip olmaz. `readonly` değiştiricisini otomatik uygulanan bir özellik ayarlayıcısına veya okuma/yazma otomatik uygulanan özelliğine ekleyemezsiniz.

## <a name="ref-readonly-return-example"></a>Ref ReadOnly dönüş örneği

`ref return` `readonly` değiştiricisi döndürülen başvurunun değiştirilemeyeceğini gösterir. Aşağıdaki örnek, kaynağına bir başvuru döndürür. Çağıranların kaynağı değiştiremeyeceğini belirtmek için `readonly` değiştiricisini kullanır:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Döndürülen türün bir `readonly struct`olması gerekmez. `ref` tarafından döndürülebilecek herhangi bir tür, `ref readonly`tarafından döndürülebilir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Dil belirtimi tekliflerini de görebilirsiniz:

- [ReadOnly ref ve ReadOnly yapısı](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [ReadOnly struct üyeleri](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](modifiers.md)
- [const](const.md)
- [Alanlar](../../programming-guide/classes-and-structs/fields.md)
