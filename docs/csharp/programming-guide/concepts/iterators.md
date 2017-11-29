---
title: Yineleyiciler (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d4994ea57d9fd0df8dfca7ffa40c280499caee6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iterators-c"></a>Yineleyiciler (C#)
Bir *yineleyici* koleksiyonlarına listeler ve dizi gibi adım için kullanılabilir.  
  
 İterator yöntemi veya `get` erişimci gerçekleştiren özel bir yineleme içinde bir koleksiyon. İterator yöntemi kullanır [verim return](../../../csharp/language-reference/keywords/yield.md) her öğeye aynı anda geri dönmek için deyimi. Zaman bir `yield return` deyimi ulaşıldığında geçerli kod konumda anımsanacak. Yürütme o konumdan yineleyici işlevi bir sonraki zamana yeniden başlatılır.  
  
 İle yineleyici istemci kodundan kullanmasını bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi veya bir LINQ Sorgu kullanarak.  
  
 Aşağıdaki örnekte, ilk yinelemesi `foreach` döngüye neden olur, devam etmek yürütme `SomeNumbers` yineleyici yöntemi ilk kadar `yield return` deyimi ulaşıldığında. Bu yineleme 3 değerini döndürür ve yineleyici yöntemi geçerli konumda korunur. Döngü sonraki yinelemesinde nereden yürütülmeye yineleyici yönteminde ulaştığında yeniden durdurma kapalı, solda bir `yield return` deyimi. Bu yineleme 5 değerini döndürür ve yineleyici yöntemi geçerli konuma yeniden korunur. Yineleyici yönteminin sonuna gelindiğinde döngü tamamlar.  
  
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
  
 Yineleyici yönteminin dönüş türü veya `get` erişimci olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Kullanabileceğiniz bir `yield break` yinelemeyi sonlandırmak için deyimi.  
  
 Yineleyiciler C# Visual Studio 2005'te tanıtıldı.  
  
 **Bu konudaki**  
  
-   [Basit yineleyici](#BKMK_SimpleIterator)  
  
-   [Koleksiyon sınıfı oluşturma](#BKMK_CollectionClass)  
  
-   [Yineleyiciler genel bir listesi ile kullanma](#BKMK_GenericList)  
  
-   [Sözdizimi bilgileri](#BKMK_SyntaxInformation)  
  
-   [Teknik uygulama](#BKMK_Technical)  
  
-   [Yineleyiciler kullanımı](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Bu konuda basit yineleyici örnek dışındaki tüm örnekler için dahil [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri için `System.Collections` ve `System.Collections.Generic` ad alanları.  
  
##  <a name="BKMK_SimpleIterator"></a>Basit yineleyici  
 Aşağıdaki örnek bir tek sahip `yield return` içinde deyimi bir [için](../../../csharp/language-reference/keywords/for.md) döngü. İçinde `Main`, her yinelemesinden `foreach` deyimi gövde oluşturur diğerine geçer yineleyici işlevi çağrısı `yield return` deyimi.  
  
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
  
##  <a name="BKMK_CollectionClass"></a>Koleksiyon sınıfı oluşturma  
 Aşağıdaki örnekte, `DaysOfTheWeek` uygulayan sınıf <xref:System.Collections.IEnumerable> gerektirir arabirimi bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi. Derleyici örtülü olarak çağırır `GetEnumerator` döndürür yöntemi bir <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Yöntemi döndürür her dize aynı anda kullanarak `yield return` deyimi.  
  
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
  
 Aşağıdaki örnekte bir `Zoo` hayvanlar koleksiyonunu içeren sınıf.  
  
 `foreach` Sınıf örneğine başvuruda bulunan deyimi (`theZoo`) örtük olarak çağırır `GetEnumerator` yöntemi. `foreach` Başvurmak deyimleri `Birds` ve `Mammals` özelliklerini kullanmak `AnimalsForType` yineleyici yöntemi adı.  
  
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
  
##  <a name="BKMK_GenericList"></a>Yineleyiciler genel bir listesi ile kullanma  
 Aşağıdaki örnekte, `Stack(Of T)` genel bir sınıf uygular <xref:System.Collections.Generic.IEnumerable%601> genel arabirim. `Push` Yöntemi atar değerleri türünde bir dizi `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Yöntemi kullanarak dizi değerleri döndürür `yield return` deyimi.  
  
 Genel yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi, genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> gerekir ayrıca uygulanan yöntemi. Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable>. Genel olmayan uygulama genel uygulamasını erteler.  
  
 Örnek veri aynı koleksiyonu yineleme yapma çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır. Bunlar yineleyiciler adlı `TopToBottom` ve `BottomToTop` özelliklerini ve `TopN` yöntemi.  
  
 `BottomToTop` Özelliği kullanan bir yineleyici bir `get` erişimcisi.  
  
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
    // foreach is allowed because theStack implements  
    // IEnumerable<int>.  
    foreach (int number in theStack)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    // foreach is allowed, because theStack.TopToBottom  
    // returns IEnumerable(Of Integer).  
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
  
##  <a name="BKMK_SyntaxInformation"></a>Sözdizimi bilgileri  
 Yineleyici bir yöntem olarak oluşabilir veya `get` erişimcisi. Yineleyici bir olay, örnek oluşturucusu, statik Oluşturucusu veya statik sonlandırıcıyı gerçekleşemez.  
  
 Örtük bir dönüştürme ifadesi türden bulunmalıdır `yield return` yineleyici dönüş türü bildirimi.  
  
 C# ' ta yineleyici yöntemi içeremez `ref` veya `out` parametreleri.  
  
 C# ' ta, "Verim" ayrılmış bir sözcük değildir ve yalnızca önce kullanıldığında, özel bir anlamı olan bir `return` veya `break` anahtar sözcüğü.  
  
##  <a name="BKMK_Technical"></a>Teknik uygulama  
 Yineleyici bir yöntem olarak yazma rağmen derleyici, iç içe geçmiş sınıf diğer bir deyişle, etkin, Durum makinesi çevirir. Bu sınıf olarak uzun yineleyici konumunu izler `foreach` istemci kodu döngüde devam eder.  
  
 Derleyici yaptıklarını görmek için bir yineleyici yöntemi için oluşturulan Microsoft Ara dil kodu görüntülemek için Ildasm.exe Aracı'nı kullanabilirsiniz.  
  
 Yineleyici için oluşturduğunuzda bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md), tüm uygulama gerekmez <xref:System.Collections.IEnumerator> arabirimi. Derleyici yineleyici algılarsa, otomatik olarak oluşturur `Current`, `MoveNext`, ve `Dispose` yöntemlerinin <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> arabirimi.  
  
 Art arda gelen her yinelemesinden üzerinde `foreach` döngü (veya doğrudan çağrısı `IEnumerator.MoveNext`), sonraki yineleyici kod gövdesi önceki sonra sürdürür `yield return` deyimi. Sonraki devam edip `yield return` yineleyici gövde sonuna ulaşılana kadar deyimi veya kadar bir `yield break` deyimi karşılaştı.  
  
 Yineleyiciler desteklemez <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi. Baştan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.  
  
 Ek bilgi için bkz: [C# dil belirtimi](../../../csharp/language-reference/language-specification/index.md).  
  
##  <a name="BKMK_UseOfIterators"></a>Yineleyiciler kullanımı  
 Yineleyiciler basitliği korumanıza olanak tanır bir `foreach` döngü listesi sırası doldurmak için karmaşık kodlar kullanmanız gerektiğinde. Aşağıdakileri yapmak istediğinizde bu yararlı olabilir:  
  
-   Sonra ilk listesi değişiklik `foreach` döngü yineleme.  
  
-   Büyük bir liste ilk yinelemesi önce tam olarak yüklenmesini önlemek bir `foreach` döngü. Bir grup tablo satır yüklemek için disk belleğine alınan fetch örneğidir. Başka bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> .NET Framework içinde yineleyiciler uygulayan yöntemi.  
  
-   Yineleyici listesini derlerken kapsüller. Yineleyici yönteminde listesi oluşturun ve her bir döngü sonucu verecek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [foreach,](../../../csharp/language-reference/keywords/foreach-in.md)  
 [uyarı simgesi](../../../csharp/language-reference/keywords/yield.md)  
 [Dizilerle foreach kullanma](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
 [Genel türler](../../../csharp/programming-guide/generics/index.md)
