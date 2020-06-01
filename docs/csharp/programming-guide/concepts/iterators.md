---
title: "C 'deki koleksiyonlar arasında yineleme #"
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 15b77fd11c0ff606119425ec7aae8e7127315e82
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240700"
---
# <a name="iterators-c"></a>Yineleyiciler (C#)

Bir *Yineleyici* , listeler ve diziler gibi koleksiyonlardan dolaşmak için kullanılabilir.

Yineleyici yöntemi veya `get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Yineleyici yöntemi, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır. Bir `yield return` ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır. Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.

Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi veya bir LINQ sorgusu kullanarak istemci kodundan bir yineleyici tüketin.

Aşağıdaki örnekte, döngünün ilk yinelemesi `foreach` yürütmenin `SomeNumbers` ilk ifadeye ulaşılana kadar yineleyici yönteminde devam etmesine neden olur `yield return` . Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur. Döngünün bir sonraki yinelemesinde, yineleyici yönteminde yürütme kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `yield return` . Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yeniden korunur. Yineleyici yönteminin sonuna ulaşıldığında döngü tamamlanır.

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

Bir yineleyici yönteminin veya erişimcisinin dönüş türü `get` <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .

`yield break`Yinelemeyi sonlandırmak için bir ifade kullanabilirsiniz.

> [!NOTE]
> Bu konudaki basit Yineleyici örneği hariç tüm örneklerde, [using](../../language-reference/keywords/using-directive.md) `System.Collections` ve ad alanları için using yönergelerini dahil edin `System.Collections.Generic` .

## <a name="simple-iterator"></a>Basit Yineleyici

Aşağıdaki örnek, `yield return` [for](../../language-reference/keywords/for.md) döngüsü içindeki tek bir ifadeye sahiptir. ' De `Main` , `foreach` ifade gövdesinin her yinelemesi bir sonraki ifadeye devam eden Yineleyici işlevine bir çağrı oluşturur `yield return` .

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

Aşağıdaki örnekte, `DaysOfTheWeek` sınıfı <xref:System.Collections.IEnumerable> bir yöntemi gerektiren arabirimini uygular <xref:System.Collections.IEnumerable.GetEnumerator%2A> . Derleyici, `GetEnumerator` bir döndüren yöntemini dolaylı olarak çağırır <xref:System.Collections.IEnumerator> .

`GetEnumerator`Yöntemi, yöntemini kullanarak her bir dizeyi bir kez döndürür `yield return` .

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

Aşağıdaki örnek, `Zoo` hayvanlar koleksiyonunu içeren bir sınıf oluşturur.

`foreach`Sınıf örneğine () başvuran ifade, `theZoo` yöntemi örtük olarak çağırır `GetEnumerator` . `foreach` `Birds` Ve özelliklerine başvuran deyimler `Mammals` `AnimalsForType` adlandırılmış yineleyici yöntemini kullanır.

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

Aşağıdaki örnekte, <xref:System.Collections.Generic.Stack%601> Genel sınıf <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini uygular. <xref:System.Collections.Generic.Stack%601.Push%2A>Yöntemi, türü bir diziye değerler atar `T` . <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Yöntemi, ifadesini kullanarak dizi değerlerini döndürür `yield return` .

Genel yöntemin yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemin de uygulanması gerekir. Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> öğesinden devralmasıdır <xref:System.Collections.IEnumerable> . Genel olmayan uygulama genel uygulamaya erteler.

Örnek, aynı veri topluluğunda tekrarların çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır. Bu adlandırılmış yineleyiciler, `TopToBottom` ve `BottomToTop` özellikleridir ve `TopN` yöntemidir.

`BottomToTop`Özelliği, bir erişimcide yineleyici kullanır `get` .

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

Yineleyici bir yöntem veya erişimci olarak gerçekleşebilir `get` . Bir olay, örnek Oluşturucu, statik oluşturucu veya statik sonlandırıcının içinde bir yineleyici gerçekleşemez.

Deyimdeki ifade türünden, `yield return` Yineleyici tarafından döndürülen için tür bağımsız değişkenine örtük bir dönüştürme bulunmalıdır `IEnumerable<T>` .

C# ' de, yineleyici yöntemi herhangi bir `in` , `ref` veya parametresine sahip olamaz `out` .

C# dilinde, `yield` ayrılmış bir sözcük değildir ve yalnızca bir `return` veya anahtar sözcüğünden önce kullanıldığında özel anlamı vardır `break` .

## <a name="technical-implementation"></a>Teknik Uygulama

Bir yineleyici Yöntem olarak yazdığınızda, derleyici onu bir durum makinesi olan bir iç içe geçmiş sınıfa çevirir. Bu sınıf, `foreach` istemci kodundaki döngü devam ettiğinde yineleyicinin konumunu izler.

Derleyicinin ne yaptığını görmek için, bir yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntülemek için ıldadsm. exe aracını kullanabilirsiniz.

Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/builtin-types/struct.md)için Yineleyici oluşturduğunuzda, tüm arabirimini uygulamanız gerekmez <xref:System.Collections.IEnumerator> . Derleyici yineleyiciyi algıladığında, `Current` `MoveNext` veya arabiriminin,, ve yöntemlerini otomatik olarak oluşturur `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .

Döngünün art arda her tekrarında `foreach` (veya doğrudan çağrısının `IEnumerator.MoveNext` ), sonraki Yineleyici kod gövdesi önceki deyimden sonra devam eder `yield return` . Daha sonra `yield return` Yineleyici gövdesinin sonuna ulaşılana kadar veya bir deyime ulaşılana kadar sonraki ifadeye devam eder `yield break` .

Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi desteklemiyor. Başlangıçtan itibaren yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir. <xref:System.Collections.IEnumerator.Reset%2A>Yineleyici yöntemi tarafından döndürülen yineleyicinin çağrılması bir oluşturur <xref:System.NotSupportedException> .

Daha fazla bilgi için bkz. [C# dil belirtimi](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Yineleyicilerin kullanımı

Yineleyiciler, `foreach` bir liste dizisini doldurmak için karmaşık kod kullanmanız gerektiğinde bir döngünün basitliğini korumanıza olanak sağlar. Bu, aşağıdakileri yapmak istediğinizde yararlı olabilir:

- İlk döngü yinelemeden sonra liste sırasını değiştirin `foreach` .

- Bir döngünün ilk yinelemesinden önce büyük bir listenin tam olarak yüklenmesini önleyin `foreach` . Tablo satırlarını toplu olarak yüklemek için disk belleğine alınmış bir getirme örneği. <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>.Net ' te yineleyiciler uygulayan yöntemi başka bir örnektir.

- Yineleyici içinde listenin oluşturulmasını yalıt. Yineleyici yönteminde, listeyi derleyip her sonucu bir döngüde sağlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Dizilerle foreach kullanma](../arrays/using-foreach-with-arrays.md)
- [Genel Türler](../generics/index.md)
