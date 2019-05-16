---
title: C# dilinde koleksiyonlar üzerinden yineleme yapma
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 931f0662b71b4dd99ac4a419c279be5058c61e92
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635516"
---
# <a name="iterators-c"></a>Yineleyiciler (C#)

Bir *yineleyici* koleksiyonlarına listeler ve diziler gibi adım için kullanılabilir.

Yineleyici yöntemini veya `get` erişimci bir koleksiyon üzerinde özel yineleme gerçekleştirir. Yineleyici yöntemini kullanır [yield return](../../../csharp/language-reference/keywords/yield.md) her öğeyi bir defada döndürmek için deyimi. Olduğunda bir `yield return` deyimine ulaşıldığında, kodun geçerli konumu anımsanacak. Yürütme, yineleyici işlevinin bir sonraki zamana o konumdan başlatılır.

Kullanarak bir yineleyici istemci kodundan kullanmak bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimini veya LINQ sorgusu kullanarak.

Aşağıdaki örnekte, ilk yinelemeyi `foreach` döngüye neden oluyor, devam etmek yürütme `SomeNumbers` yineleyici yöntemin ilk kadar `yield return` deyimine ulaşıldığında. Bu yineleme 3 değerini döndürür ve yineleyici yöntem geçerli konumu korunur. Döngüsünün sonraki yinelemesinde, yineleyici yöntemin yürütülmesine kadar devam eder, ulaştığında yeniden kaldığı bir `yield return` deyimi. Bu yineleme 5 değerini döndürür ve yineleyici yöntem geçerli konumu tekrar korunur. Yineleyici yöntemin sonuna ulaşıldığında döngüsünü tamamlar.

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

Bir yineleyici yöntemin dönüş türü veya `get` erişimcisi olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.

Kullanabileceğiniz bir `yield break` yinelemeyi sonlandırmak için deyimi.

> [!NOTE]
> Bu konuda, basit bir yineleyici örnek hariç tüm örnekler için dahil [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri `System.Collections` ve `System.Collections.Generic` ad alanları.

## <a name="simple-iterator"></a>Basit bir yineleyici

Aşağıdaki örnek, tek bir sahip `yield return` içindeki bir [için](../../../csharp/language-reference/keywords/for.md) döngü. İçinde `Main`, her bir yinelemesini `foreach` diğerine geçer yineleyici işlevine bir çağrı oluşturur ve deyim gövdesi `yield return` deyimi.

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a>Koleksiyon sınıfı oluşturma

Aşağıdaki örnekte, `DaysOfTheWeek` sınıfının Implements <xref:System.Collections.IEnumerable> gerektiren arabirimi bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi. Derleyici örtük olarak çağırır `GetEnumerator` döndüren yöntemi bir <xref:System.Collections.IEnumerator>.

`GetEnumerator` Yöntemi döndürür her dize bir kerede kullanarak `yield return` deyimi.

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

Aşağıdaki örnek, oluşturur bir `Zoo` hayvanlar koleksiyonunu içeren sınıf.

`foreach` Sınıfı örneğini ifade deyimi (`theZoo`) örtük olarak çağırır `GetEnumerator` yöntemi. `foreach` Başvurmak ifadeleri `Birds` ve `Mammals` özellikleri kullanım `AnimalsForType` yineleyici yöntemin adı.

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a>Yineleyiciler genel listeyle kullanma

Aşağıdaki örnekte, <xref:System.Collections.Generic.Stack%601> genel bir sınıf uygulayan <xref:System.Collections.Generic.IEnumerable%601> genel arabirim. <xref:System.Collections.Generic.Stack%601.Push%2A> Yöntemi, bir dizi türüne değerleri atar `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Yöntemi kullanarak dizi değerlerini döndürür `yield return` deyimi.

Genel yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntem, genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi de uygulanmalı. Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable>. Genel olmayan uygulama için genel uygulamasını erteler.

Örneğin, verilerin aynı koleksiyon aracılığıyla yineleme çeşitli yöntemler desteklemek için adlandırılmış yineleyiciler kullanır. Bunlar yineleyiciler adlı `TopToBottom` ve `BottomToTop` özellikleri ve `TopN` yöntemi.

`BottomToTop` Özelliği kullanan bir yineleyici içinde bir `get` erişimcisi.

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a>Söz dizimi bilgileri

Yineleyici yöntem olarak oluşabilir veya `get` erişimcisi. Bir yineleyiciyi bir olay, örnek oluşturucusu, statik oluşturucu veya statik Sonlandırıcı oluşamaz.

Örtük bir dönüştürme ifadesi türden bulunmalıdır `yield return` IEnumerable tür bağımsız değişkeni ifadesine\<T > döndürülen yineleyici tarafından.

C# ' ta bir yineleyici yöntemini içeremez `in`, `ref`, veya `out` parametreleri.

C# ' ta, "yield" ayrılmış bir sözcük değildir ve yalnızca önce kullanıldığında özel anlamı bir `return` veya `break` anahtar sözcüğü.

## <a name="technical-implementation"></a>Teknik Uygulama

Bir yöntem olarak bir yineleyici yazma olsa da, derleyici, iç içe geçmiş bir sınıf içinde başka bir deyişle, aslında bir Durum makinesi çevirir. Bu sınıf olarak uzun yineleyici konumunu izler `foreach` istemci kodu döngüde devam eder.

Derleyicinin ne yaptığını görmek için bir yineleyici yöntem için oluşturulan Microsoft Ara dil kodunu görüntülemek için Ildasm.exe Aracı'nı kullanabilirsiniz.

İçin bir yineleyici oluşturduğunuzda bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md), tam uygulamanız gerekmez <xref:System.Collections.IEnumerator> arabirimi. Derleyici yineleyici algıladığında otomatik olarak oluşturduğu `Current`, `MoveNext`, ve `Dispose` yöntemlerinin <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> arabirimi.

Her yinelemede üzerinde `foreach` döngü (veya doğrudan arama `IEnumerator.MoveNext`), İleri yineleyici kod gövdesi önceki sonra sürdürür `yield return` deyimi. Daha sonra bir sonraki sürdürür `yield return` yineleyici gövdenin sonuna ulaşılana kadar bir deyimi veya kadar bir `yield break` deyimi karşılaştı.

Yineleyicileri desteklemez <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi. Başlangıçtan itibaren yinelemek için yeni bir yineleyici edinmeniz gerekir. Çağırma <xref:System.Collections.IEnumerator.Reset%2A> üzerinde bir yineleyici yöntem tarafından döndürülen yineleyici oluşturur bir <xref:System.NotSupportedException>.

Ek bilgi için bkz: [C# dil belirtimi](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Yineleyicilerin kullanın

Yineleyiciler basitliğinin korumak etkinleştirme bir `foreach` döngü listesi sırası doldurmak için karmaşık kodlar kullanmanız gerektiğinde. Aşağıdakileri yapmak istediğinizde bu yararlı olabilir:

- Liste sonra ilk dağıtmayın `foreach` döngü yinelemesi.

- Büyük bir liste ilk yinelemeyi önce tam olarak yüklenmesini önlemek bir `foreach` döngü. Tablo satırları toplu yükleme için disk belleğine alınan fetch buna bir örnektir. Başka bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> yineleyiciler .NET Framework içindeki uygulayan yöntemi.

- Yineleyici listesinde oluşturmaya kapsüller. Yineleyici yöntem içinde listesi oluşturmak ve ardından her bir döngü sonucu verecek.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)
- [yield](../../../csharp/language-reference/keywords/yield.md)
- [Dizilerle foreach kullanma](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)
