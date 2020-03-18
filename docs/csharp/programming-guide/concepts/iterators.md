---
title: "C'deki koleksiyonlar aracılığıyla iterate #"
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626276"
---
# <a name="iterators-c"></a>Yineleyiciler (C#)

Listeler ve diziler gibi koleksiyonlarda adım atmak için bir *yineleyici* kullanılabilir.

Bir yineleyici yöntemi `get` veya erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Yineleyici yöntemi, her öğeyi birer birer döndürmek için [verim iade](../../language-reference/keywords/yield.md) deyimini kullanır. Bir `yield return` bildirime ulaşıldığında, koddaki geçerli konum hatırlanır. Yürütme, yineleyici işlevi bir sonraki çağrıldığında bu konumdan yeniden başlatılır.

[Her bir forher](../../language-reference/keywords/foreach-in.md) deyimi kullanarak veya bir LINQ sorgusu kullanarak istemci kodundan bir yineleyici tüketirsiniz.

Aşağıdaki örnekte, döngünün ilk yinelemesi, ilk `foreach` `SomeNumbers` `yield return` ifadeye ulaşılına kadar yürütmenin yineleyici yönteminde ilerlemesine neden olur. Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur. Döngünün bir sonraki yinelemesinde, yineleyici yöntemindeki yürütme kaldığı yerden devam ediyor ve bir `yield return` bildirime ulaştığında yine durur. Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yine korunur. Yineleme yönteminin sonuna ulaşıldığında döngü tamamlanır.

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

Bir yineleyici yönteminin `get` veya erişime neden <xref:System.Collections.IEnumerable>olan <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>bir <xref:System.Collections.Generic.IEnumerator%601>yöntemin dönüş türü , , , veya .

Yinelemeyi sona `yield break` erdirmek için bir deyim kullanabilirsiniz.

> [!NOTE]
> Basit Yineleme örneği dışındaki bu konuyla ilgili tüm [using](../../language-reference/keywords/using-directive.md) örnekler için, `System.Collections` yönergeler ve `System.Collections.Generic` ad alanları için kullanma içerir.

## <a name="simple-iterator"></a>Basit Yineleme

Aşağıdaki örnekte `yield return` [for](../../language-reference/keywords/for.md) döngüsü içinde tek bir ifade vardır. İfade `Main`gövdesinin `foreach` her yinelemesinde, bir sonraki `yield return` deyime devam eden yineleyici işlevine bir çağrı oluşturulur.

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

## <a name="creating-a-collection-class"></a>Koleksiyon Sınıfı Oluşturma

Aşağıdaki örnekte, `DaysOfTheWeek` sınıf bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> <xref:System.Collections.IEnumerable> yöntem gerektiren arabirimi uygular. Derleyici dolaylı olarak `GetEnumerator` yöntemi çağırır ve <xref:System.Collections.IEnumerator>bu yöntem bir .

Yöntem `GetEnumerator` deyimi kullanarak `yield return` her dize yi birer birer döndürür.

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

Aşağıdaki örnek, bir `Zoo` hayvan koleksiyonu içeren bir sınıf oluşturur.

Sınıf `foreach` örneğine başvuran ifade`theZoo`( ) `GetEnumerator` dolaylı olarak yöntemi çağırır. Bu `foreach` `Birds` ifadeler ve `Mammals` özellikleri başvuran `AnimalsForType` adlandırılmış yineleyici yöntemini kullanın.

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

## <a name="using-iterators-with-a-generic-list"></a>Genel Listeyle Yinelemeleri Kullanma

Aşağıdaki örnekte, <xref:System.Collections.Generic.Stack%601> genel sınıf <xref:System.Collections.Generic.IEnumerable%601> genel arabirimi uygular. Yöntem, <xref:System.Collections.Generic.Stack%601.Push%2A> değerleri bir tür `T`dizisine atar. Yöntem <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> `yield return` deyimi kullanarak dizi değerlerini döndürür.

Genel <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yönteme ek olarak, genel <xref:System.Collections.IEnumerable.GetEnumerator%2A> olmayan yöntem de uygulanmalıdır. Bunun nedeni, 'den <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable>miras olmasıdır. Genel olmayan uygulama genel uygulamaya erteler.

Örnek, aynı veri toplama yoluyla yineleme çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır. Bu adlandırılmış `TopToBottom` yineleyiciler `BottomToTop` ve özellikleri `TopN` ve yöntemi vardır.

Özellik, `BottomToTop` bir aksesuarda bir `get` yineleyici kullanır.

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

## <a name="syntax-information"></a>Sözdizimi Bilgileri

Bir yineleyici bir yöntem veya `get` erişimci olarak oluşabilir. Bir olay, örnek oluşturucu, statik oluşturucu veya statik sonlandırıcı bir olay meydana gelemez.

`yield return` Örtük bir dönüştürme, deyimdeki ifade türünden yineleyici `IEnumerable<T>` tarafından döndürülen tür bağımsız değişkenine kadar olmalıdır.

C#'da, bir yineleyici yöntemi, `in` `ref`herhangi `out` bir , veya parametre olamaz.

C#'da `yield` ayrılmış bir sözcük değildir ve yalnızca bir `return` veya `break` anahtar kelimeden önce kullanıldığında özel bir anlamı vardır.

## <a name="technical-implementation"></a>Teknik Uygulama

Bir yöntem olarak bir yineleyici yazmanıza rağmen, derleyici bunu aslında bir durum makinesi olan iç içe geçmiş bir sınıfa çevirir. Bu sınıf, istemci kodundaki `foreach` döngü devam ettikçe yineleyicinin konumunu izler.

Derleyicinin ne yaptığını görmek için, yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntülemek için Ildasm.exe aracını kullanabilirsiniz.

Bir [sınıf](../../language-reference/keywords/class.md) veya [yapı](../../language-reference/builtin-types/struct.md)için bir yineleyici oluşturduğunuzda, tüm <xref:System.Collections.IEnumerator> arabirimi uygulamanız gerekmez. Derleyici yineleyiciyi algıladığında, otomatik `Current`olarak , ve `MoveNext` `Dispose` yöntemleri veya <xref:System.Collections.IEnumerator> arabirimi <xref:System.Collections.Generic.IEnumerator%601> oluşturur.

Döngünün (veya doğrudan `foreach` çağrının) birbirini izleyen `IEnumerator.MoveNext`her yinelemesinde, bir sonraki yineleyici `yield return` kodu gövdesi önceki deyimden sonra devam eder. Daha sonra, yineleme `yield return` gövdesinin sonuna ulaşılınceye veya bir ifadeyle `yield break` karşılaşına kadar bir sonraki ifadeye devam edilir.

Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi desteklemez. Baştan yinelemek için, yeni bir yineleyici edinmeniz gerekir. Bir <xref:System.Collections.IEnumerator.Reset%2A> yineleyici yöntemi yle döndürülen yineleyiciyi çağırmak <xref:System.NotSupportedException>bir .

Daha fazla bilgi için [C# Dil Belirtimi'ne](~/_csharplang/spec/classes.md#iterators)bakın.

## <a name="use-of-iterators"></a>Yinelemelerin Kullanımı

Yineleyiciler, liste sırasını doldurmak için `foreach` karmaşık kod kullanmanız gerektiğinde döngünün basitliğini korumanızı sağlar. Aşağıdakileri yapmak istediğinizde bu yararlı olabilir:

- İlk `foreach` döngü yinelemeden sonra liste sırasını değiştirin.

- Bir `foreach` döngünün ilk yinelemesinden önce büyük bir listeyi tam olarak yüklemekten kaçının. Bir örnek, bir tablo satırı toplu yüklemek için çağrılı getir. Başka bir <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> örnek, .NET Çerçevesi içinde yineleyicileri uygulayan yöntemdir.

- Listeyi yineleyicide oluşturmayı kapsüller. Yineleyici yönteminde, listeyi oluşturabilir ve sonra her sonucu bir döngüde verebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Dizilerle foreach kullanma](../arrays/using-foreach-with-arrays.md)
- [Genel Türler](../generics/index.md)
