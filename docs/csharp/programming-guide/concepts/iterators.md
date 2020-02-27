---
title: İçindeki koleksiyonlar arasında yinelemeC#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626276"
---
# <a name="iterators-c"></a>Yineleyiciler (C#)

Bir *Yineleyici* , listeler ve diziler gibi koleksiyonlardan dolaşmak için kullanılabilir.

Yineleyici yöntemi veya `get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Yineleyici yöntemi, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır. `yield return` ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır. Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.

Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi veya bir LINQ sorgusu kullanarak istemci kodundan bir yineleyici tüketin.

Aşağıdaki örnekte, ilk `yield return` ifadeye ulaşılana kadar `foreach` döngüsünün ilk yinelemesi yürütmenin `SomeNumbers` yineleyici yönteminde devam etmesine neden olur. Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur. Döngünün bir sonraki yinelemesinde, yineleyici yönteminde yürütme kaldığınız yerden devam eder, bir `yield return` bildirimine ulaştığında yeniden durdurulur. Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yeniden korunur. Yineleyici yönteminin sonuna ulaşıldığında döngü tamamlanır.

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

Yineleyici yöntemi veya `get` erişimcisinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olabilir.

Yinelemeyi sonlandırmak için `yield break` bir ifade kullanabilirsiniz.

> [!NOTE]
> Bu konudaki basit Yineleyici örneği hariç tüm örneklerde, `System.Collections` ve `System.Collections.Generic` ad alanları için [using](../../language-reference/keywords/using-directive.md) yönergelerini dahil edin.

## <a name="simple-iterator"></a>Basit Yineleyici

Aşağıdaki örnek, [for](../../language-reference/keywords/for.md) döngüsü içindeki tek bir `yield return` bildirimine sahiptir. `Main`, `foreach` deyimin gövdesinin her yinelemesi, bir sonraki `yield return` ifadesine devam eden Yineleyici işlevine bir çağrı oluşturur.

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

Aşağıdaki örnekte, `DaysOfTheWeek` sınıfı bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi gerektiren <xref:System.Collections.IEnumerable> arabirimini uygular. Derleyici, bir <xref:System.Collections.IEnumerator>döndüren `GetEnumerator` yöntemini örtülü olarak çağırır.

`GetEnumerator` yöntemi her bir dizeyi her bir kez `yield return` ifadesini kullanarak döndürür.

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

Aşağıdaki örnek, hayvanlar koleksiyonu içeren bir `Zoo` sınıfı oluşturur.

Sınıf örneğine (`theZoo`) başvuran `foreach` ifade `GetEnumerator` yöntemini örtülü olarak çağırır. `Birds` ve `Mammals` özelliklerine başvuran `foreach` deyimleri, `AnimalsForType` adlı yineleyici yöntemini kullanır.

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

## <a name="using-iterators-with-a-generic-list"></a>Bir genel liste ile yineleyiciler kullanma

Aşağıdaki örnekte, <xref:System.Collections.Generic.Stack%601> genel sınıfı <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini uygular. <xref:System.Collections.Generic.Stack%601.Push%2A> yöntemi `T`türünde bir diziye değerler atar. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi `yield return` ifadesini kullanarak dizi değerlerini döndürür.

Genel <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoduna ek olarak, genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin da uygulanması gerekir. Bunun nedeni <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable>devralmasıdır. Genel olmayan uygulama genel uygulamaya erteler.

Örnek, aynı veri topluluğunda tekrarların çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır. Bu adlandırılmış yineleyiciler `TopToBottom` ve `BottomToTop` özelliklerdir ve `TopN` yöntemidir.

`BottomToTop` özelliği bir `get` erişimcisinde yineleyici kullanır.

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

## <a name="syntax-information"></a>Sözdizimi bilgileri

Yineleyici, bir yöntem veya `get` erişimcisi olarak gerçekleşebilir. Bir olay, örnek Oluşturucu, statik oluşturucu veya statik sonlandırıcının içinde bir yineleyici gerçekleşemez.

`yield return` deyimindeki ifade türünden örtük bir dönüştürme, Yineleyici tarafından döndürülen `IEnumerable<T>` tür bağımsız değişkenine sahip olmalıdır.

' C#De, bir yineleyici yönteminde `in`, `ref`veya `out` parametreleri olamaz.

İçinde C#, `yield` ayrılmış bir sözcük değildir ve yalnızca bir `return` veya `break` anahtar sözcüğünden önce kullanıldığında özel anlamı vardır.

## <a name="technical-implementation"></a>Teknik Uygulama

Bir yineleyici Yöntem olarak yazdığınızda, derleyici onu bir durum makinesi olan bir iç içe geçmiş sınıfa çevirir. Bu sınıf, istemci kodundaki `foreach` döngüsünün devam ettiği sürece yineleyicinin konumunu izler.

Derleyicinin ne yaptığını görmek için, bir yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntülemek için ıldadsm. exe aracını kullanabilirsiniz.

Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/builtin-types/struct.md)için yineleyici oluşturduğunuzda, tüm <xref:System.Collections.IEnumerator> arabirimini uygulamanız gerekmez. Derleyici yineleyiciyi algıladığında, <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> arabiriminin `Current`, `MoveNext`ve `Dispose` yöntemlerini otomatik olarak oluşturur.

`foreach` döngüsünün art arda her tekrarında (veya doğrudan `IEnumerator.MoveNext`çağrısı), sonraki Yineleyici kod gövdesi önceki `yield return` deyimden sonra devam eder. Daha sonra Yineleyici gövdesinin sonuna ulaşılana kadar veya bir `yield break` ifadesiyle karşılaşana kadar sonraki `yield return` bildirimine devam eder.

Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metodunu desteklemez. Başlangıçtan itibaren yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir. Yineleyici yöntemi tarafından döndürülen yineleyicinin <xref:System.Collections.IEnumerator.Reset%2A> çağrılması bir <xref:System.NotSupportedException>oluşturur.

Daha fazla bilgi için bkz. [ C# dil belirtimi](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Yineleyicilerin kullanımı

Yineleyiciler, bir liste dizisini doldurmak için karmaşık kod kullanmanız gerektiğinde `foreach` döngüsünün basitliğini korumanıza olanak sağlar. Bu, aşağıdakileri yapmak istediğinizde yararlı olabilir:

- İlk `foreach` döngüsü yinelemeden sonra liste sırasını değiştirin.

- `foreach` döngüsünün ilk yinelemesinden önce büyük bir listenin tam olarak yüklenmesini önleyin. Tablo satırlarını toplu olarak yüklemek için disk belleğine alınmış bir getirme örneği. Başka bir örnek, .NET Framework içinde yineleyiciler uygulayan <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> yöntemidir.

- Yineleyici içinde listenin oluşturulmasını yalıt. Yineleyici yönteminde, listeyi derleyip her sonucu bir döngüde sağlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Dizilerle foreach kullanma](../arrays/using-foreach-with-arrays.md)
- [Genel Türler](../generics/index.md)
