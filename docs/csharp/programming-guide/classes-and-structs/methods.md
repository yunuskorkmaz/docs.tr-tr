---
title: Yöntemler-C# Programlama Kılavuzu
description: C# içindeki bir yöntem, bir dizi deyim içeren bir kod bloğudur. Program, yöntemini çağırarak ve bağımsız değişkenleri belirterek deyimleri çalıştırır.
ms.date: 03/08/2021
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: d503c394e02f6f384e63de4fcd9cc8d2eec43da0
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653510"
---
# <a name="methods-c-programming-guide"></a>Yöntemler (C# Programlama Kılavuzu)

Yöntemi, bir dizi deyim içeren bir kod bloğudur. Program, metodu çağırarak ve gerekli Yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur. C# ' de, yürütülen her yönerge bir yöntem bağlamında gerçekleştirilir.

`Main`Yöntemi her C# uygulamasının giriş noktasıdır ve program başlatıldığında ortak dil çalışma zamanı (CLR) tarafından çağırılır. [Üst düzey deyimler](../main-and-command-args/top-level-statements.md)kullanan bir uygulamada, `Main` yöntemi derleyici tarafından oluşturulur ve tüm üst düzey deyimleri içerir.

> [!NOTE]
> Bu makalede adlandırılmış yöntemler ele alınmaktadır. Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).

## <a name="method-signatures"></a>Yöntem imzaları

Yöntemler veya, [](../../language-reference/keywords/class.md) [](../../language-reference/builtin-types/struct.md) [](../interfaces/index.md) `public` `private` `abstract` `sealed` dönüş değeri, yöntemin adı ve herhangi bir yöntem parametresi gibi erişim düzeyi belirtilerek, veya gibi isteğe bağlı değiştiriciler belirtilerek bir sınıf, yapı veya arabirim içinde bildirilmiştir. Bu parçalar, yönteminin imzasıdır.

> [!IMPORTANT]
> Bir yöntemin dönüş türü, yöntem aşırı yüklemesi amaçları için yöntemin imzasının bir parçası değildir. Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğun belirlenmesi sırasında yönteminin imzasının bir parçasıdır.

Yöntem parametreleri parantez içine alınır ve virgülle ayrılır. Boş parantezler, yöntemin hiçbir parametre gerektirmediğini belirtir. Bu sınıf dört yöntem içerir:

[!code-csharp[DifferentModifiersOnMethods#1](snippets/methods/Program.cs#1)]

## <a name="method-access"></a>Yöntem erişimi

Bir nesne üzerinde bir yöntemi çağırmak, bir alana erişme gibidir. Nesne adından sonra bir nokta, yöntemin adı ve parantez ekleyin. Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır. `Motorcycle`Bu nedenle, sınıfının yöntemleri aşağıdaki örnekte olduğu gibi çağrılabilir:

[!code-csharp[CallingMethods#2](snippets/methods/Program.cs#2)]

## <a name="method-parameters-vs-arguments"></a>Yöntem parametreleri ve bağımsız değişkenler

Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir. Kodu çağırırken yöntemi çağırdığında, her parametre için bağımsız değişkenler olarak adlandırılan somut değerler sağlar. Bağımsız değişkenlerin parametre türüyle uyumlu olması gerekir, ancak çağıran kodda kullanılan bağımsız değişken adı (varsa) yöntemde tanımlanan parametre ile aynı olmalıdır. Örnek:

[!code-csharp[MethodExamples#3](snippets/methods/Program.cs#3)]

## <a name="passing-by-reference-vs-passing-by-value"></a>Başvuruya göre geçirme-değere göre geçirme

Varsayılan olarak, bir [değer türü](../../language-reference/builtin-types/value-types.md) örneği bir yönteme geçirildiğinde, kopyasının kendisi yerine geçirilir. Bu nedenle, bağımsız değişkende yapılan değişikliklerin, çağırma yönteminde orijinal örnek üzerinde hiçbir etkisi yoktur. Değer türü örneği başvuruya göre geçirmek için `ref` anahtar sözcüğünü kullanın. Daha fazla bilgi için bkz. [Value-Type parametrelerini geçirme](./passing-value-type-parameters.md).

Başvuru türündeki bir nesne yöntemine geçirildiğinde, nesnesine bir başvuru geçirilir. Diğer bir deyişle, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişken alır. Bu başvuruyu kullanarak nesnesinin bir üyesini değiştirirseniz, nesneyi değere göre iletseniz bile, değişiklik çağırma yöntemindeki bağımsız değişkende yansıtılır.

`class`Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü kullanarak bir başvuru türü oluşturursunuz:

[!code-csharp[SampleRefTypeClass#4](snippets/methods/Program.cs#4)]

Artık, bu türü temel alan bir nesneyi bir yönteme geçirirseniz, nesnesine bir başvuru geçirilir. Aşağıdaki örnek, türünde bir nesnesini yöntemine geçirir `SampleRefType` `ModifyObject` :

[!code-csharp[PassingAReferenceType#5](snippets/methods/Program.cs#5)]

Örnek temelde bir yönteme değere göre bir bağımsız değişken geçirdiğinden önceki örnekle aynı şeyi yapar. Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır. Parametresinin alanı üzerinde yapılan değişiklik, `ModifyObject` `value` `obj` `value` yöntemi içindeki bağımsız değişkenin alanını da değiştirir `rt` `TestRefType` . `TestRefType`Yöntemi çıkış olarak 33 görüntüler.

Başvuru türlerini başvuruya ve değere göre geçirme hakkında daha fazla bilgi için bkz. [Reference-Type parametrelerini](./passing-reference-type-parameters.md) ve [başvuru türlerini](../../language-reference/keywords/reference-types.md)geçirme.

## <a name="return-values"></a>Dönüş değerleri

Yöntemler çağırana bir değer döndürebilir. Dönüş türü, yöntem adından önce listelenen tür değilse, `void` yöntemi anahtar sözcüğünü kullanarak değeri döndürebilir `return` . `return`Dönüş türüyle eşleşen bir değer gelen anahtar sözcüğünü içeren bir ifade, bu değeri çağıran metoda döndürür.

Değer, çağıran değere veya C# 7,0 ile başlayarak [başvuruya göre](ref-returns.md)döndürülebilir. `ref`Anahtar sözcüğü Yöntem imzasında kullanılıyorsa ve her bir anahtar sözcüğü izliyorsa, değerler, çağıran başvuruya göre döndürülür `return` . Örneğin, aşağıdaki yöntem imzası ve Return deyimleri, yöntemin çağırana başvuruya göre değişken adlarını döndürdüğünü gösterir `estDistance` .

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

`return`Anahtar sözcüğü, yönteminin yürütülmesini de sonlandırır. Dönüş türü ise, `void` `return` değeri olmayan bir ifade, metodun yürütülmesini durdurmak için hala yararlıdır. `return`Anahtar sözcüğü olmadan Yöntem, kod bloğunun sonuna ulaştığında yürütmeyi durdurur. `return`Bir değer döndürmek için anahtar sözcüğünü kullanmak için void olmayan bir dönüş türüne sahip metotlar gereklidir. Örneğin, bu iki yöntem `return` tamsayılar döndürmek için anahtar sözcüğünü kullanır:

[!code-csharp[SimpleMathClass#6](snippets/methods/Program.cs#6)]

Bir yöntemden döndürülen bir değer kullanmak için, çağırma yöntemi yöntemi tek bir değer olan her yerde, aynı türde bir değer yeterli olacak şekilde kullanabilir. Dönüş değerini bir değişkene de atayabilirsiniz. Örneğin, aşağıdaki iki kod örneği aynı hedefi yerine getirmektedir:

[!code-csharp[SquareANumberWithAddTwoNumbersUsingLocalVariable#7](snippets/methods/Program.cs#7)]

[!code-csharp[SquareANumberWithAddTwoNumbersInTheSameLine#8](snippets/methods/Program.cs#8)]

Bu durumda, `result` bir değeri depolamak için yerel bir değişken kullanmak isteğe bağlıdır. Kodun okunabilirliğini yardımcı olabilir veya metodun tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekirse gerekli olabilir.

Bir yöntemden başvuruya göre döndürülen bir değeri kullanmak için, değerini değiştirmek istiyorsanız bir [ref yerel](ref-returns.md#ref-locals) değişkeni bildirmeniz gerekir. Örneğin, `Planet.GetEstimatedDistance` yöntemi <xref:System.Double> başvuruya göre bir değer döndürürse, bunu aşağıdaki gibi kodla bir ref yerel değişkeni olarak tanımlayabilirsiniz:

```csharp
ref int distance = plant
```

`M`Arama işlevi diziyi içine geçirse, dizinin içeriğini değiştiren bir yöntemden çok boyutlu bir dizi döndürülüyor `M` .  Elde edilen diziyi, `M` iyi stil veya işlevsel akış için öğesinden döndürebilirsiniz, ancak C# tüm başvuru türlerini değere göre geçirdiğinden ve dizi başvurusunun değeri dizi işaretçisiyse, bu gerekli değildir. Yönteminde `M` , dizinin içeriğinde yapılan tüm değişiklikler, aşağıdaki örnekte gösterildiği gibi diziye başvuran herhangi bir kod tarafından Observable ' tır:

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

Daha fazla bilgi için bkz. [Return](../../language-reference/keywords/return.md).

## <a name="async-methods"></a>Zaman uyumsuz yöntemler

Async özelliğini kullanarak, açık geri çağırmaları kullanmadan zaman uyumsuz yöntemleri çağırabilir veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde el ile böedebilirsiniz.

[Zaman uyumsuz](../../language-reference/keywords/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](../../language-reference/operators/await.md) işlecini kullanabilirsiniz. Denetim zaman uyumsuz yöntemde bir await ifadesine ulaştığında denetim çağırana döner ve beklenen görev tamamlanana kadar yöntemdeki ilerleme durumu askıya alınır. Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir.

> [!NOTE]
> Zaman uyumsuz bir yöntem, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında çağırana döner veya zaman uyumsuz yöntemin sonuna kadar, hangisi önce gerçekleşiyorsa.

Zaman uyumsuz bir yöntem genellikle, veya dönüş türüne <xref:System.Threading.Tasks.Task%601> sahiptir <xref:System.Threading.Tasks.Task> <xref:System.Collections.Generic.IAsyncEnumerable%601> `void` . `void`Dönüş türü öncelikle bir dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır `void` . Döndüren zaman uyumsuz bir yöntem beklenemez `void` ve void döndüren bir yöntemi çağıran yöntemin aldığı özel durumları yakalayamaz. C# 7,0 ile başlayarak, zaman uyumsuz bir yöntem [herhangi bir görev benzeri dönüş türüne](../../whats-new/csharp-7.md#generalized-async-return-types)sahip olabilir.

Aşağıdaki örnekte, `DelayAsync` dönüş türüne sahip bir zaman uyumsuz yöntem <xref:System.Threading.Tasks.Task%601> . `DelayAsync` , `return` bir tamsayı döndüren bir ifadeye sahiptir. Bu nedenle, öğesinin yöntem bildirimi `DelayAsync` bir dönüş türüne sahip olmalıdır `Task<int>` . Dönüş türü olduğu için `Task<int>` , `await` içindeki ifadesinin değerlendirmesi `DoSomethingAsync` aşağıdaki deyim tarafından gösterildiği gibi bir tamsayı oluşturur: `int result = await delayTask` .

`Main`Yöntemi, dönüş türüne sahip bir zaman uyumsuz metoda bir örnektir <xref:System.Threading.Tasks.Task> . `DoSomethingAsync`Yöntemine gider ve tek bir satırla ifade edildiğinden, `async` ve `await` anahtar sözcüklerini atlayabilir. `DoSomethingAsync`Zaman uyumsuz bir yöntem olduğundan, çağrının görevi `DoSomethingAsync` beklenmelidir, çünkü aşağıdaki deyimde gösterildiği gibi: `await DoSomethingAsync();` .

:::code language="csharp" source="snippets/classes-and-structs/methods/Program.cs":::

Zaman uyumsuz bir yöntem herhangi bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi bildiremez, ancak bu parametrelere sahip yöntemleri çağırabilir.

Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. Async ve await ile zaman uyumsuz [dönüş türleri](../concepts/async/async-return-types.md) [ile zaman uyumsuz programlama](../concepts/async/index.md) .

## <a name="expression-body-definitions"></a>İfade gövdesi tanımları

Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir deyimi olan yöntem tanımlarının olması yaygındır. Kullanarak bu tür yöntemleri tanımlamaya yönelik bir sözdizimi kısayolu vardır `=>` :

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Yöntemi `void` bir zaman uyumsuz yöntem döndürürse veya ise, yöntemin gövdesi bir deyim ifadesi olmalıdır (Lambdalar ile aynı). Özellikler ve Dizin oluşturucular için, bunların salt okunmaları ve `get` erişimci anahtar sözcüğünü kullanmanız gerekir.

## <a name="iterators"></a>Yineleyiciler

Yineleyici, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir. Bir yineleyici, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır. Bir [yield return](../../language-reference/keywords/yield.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır. Yineleyici bir sonraki sefer çağrıldığında, yürütme o konumdan yeniden başlatılır.

Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi kullanarak istemci kodundan bir yineleyici çağırın.

Yineleyicinin dönüş türü <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .

Daha fazla bilgi için bkz. [yineleyiciler](../concepts/iterators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](static-classes-and-static-class-members.md)
- [Devralma](inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [return](../../language-reference/keywords/return.md)
- [out](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [Parametreleri Geçirme](passing-parameters.md)
