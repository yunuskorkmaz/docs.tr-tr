---
title: Varyant Genel Arabirimler Oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595312"
---
# <a name="creating-variant-generic-interfaces-c"></a>Varyant Genel Arabirimler Oluşturma (C#)

Arabirimlerdeki genel tür parametrelerini ortak değişken veya zıt değişken olarak bildirebilirsiniz. *Covariance,* arabirim yöntemlerinin genel tür parametreleri tarafından tanımlanandan daha fazla türemiş iade türüne sahip olmasını sağlar. *Kontravariance,* arabirim yöntemlerinin genel parametrelertarafından belirtilenden daha az türemiş bağımsız değişken türlerine sahip olmasını sağlar. Ortak veya kontravariant genel tür parametrelerine sahip genel arabirim *varyant*olarak adlandırılır.

> [!NOTE]
> .NET Framework 4, varolan birkaç genel arabirim için varyans desteği sundu. .NET Framework'deki varyant arabirimlerinin listesi için [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)bölümüne bakın.

## <a name="declaring-variant-generic-interfaces"></a>Varyant Genel Arabirimleri Bildirme

Genel tür parametreleri için anahtar `in` `out` kelimeleri ve anahtar kelimeleri kullanarak varyant genel arabirimleri bildirebilirsiniz.

> [!IMPORTANT]
> `ref`, `in`, `out` ve C# parametreleri varyant olamaz. Değer türleri de varyansı desteklemez.

Anahtar kelimeyi kullanarak genel bir tür `out` parametre eşdeğişkenini bildirebilirsiniz. Ortak varyant türü aşağıdaki koşulları karşılamalıdır:

- Tür yalnızca arabirim yöntemlerinin bir dönüş türü olarak kullanılır ve yöntem bağımsız değişkenleri türü olarak kullanılmaz. Bu, türün `R` eşdeğişken olarak ilan edildiği aşağıdaki örnekte gösterilmiştir.

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    Bu kuralın bir istisnası vardır. Yöntem parametresi olarak karşıt genel temsilciniz varsa, temsilci için genel tür parametresi olarak türü kullanabilirsiniz. Bu, aşağıdaki örnekteki türe `R` göre gösterilmiştir. Daha fazla bilgi için, [Varyans In Delegates (C#)](./variance-in-delegates.md) ve [Func ve Action Generic Delegates (C#) için Varyans kullanma'ya](./using-variance-for-func-and-action-generic-delegates.md)bakın.

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- Tür, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz. Bu, aşağıdaki kodda gösterilmiştir.

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

Anahtar kelimeyi kullanarak genel bir tür `in` parametre karşıtdeğişkenini bildirebilirsiniz. Karşıt tür, arabirim yöntemlerinin geri dönüş türü olarak değil, yalnızca yöntem bağımsız değişkenleri türü olarak kullanılabilir. Karşıt değişken türü genel kısıtlamalar için de kullanılabilir. Aşağıdaki kod, karşıt arabirimi nasıl bildireceklerini ve yöntemlerinden biri için genel bir kısıtlamanın nasıl kullanılacağını gösterir.

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

Aynı arabirimde hem covariance hem de contravariance'ı desteklemek de mümkündür, ancak aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri için.

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a>Varyant Genel Arabirimlerin Uygulanması

Değişmez arabirimler için kullanılan aynı sözdizimini kullanarak sınıflarda varyant genel arabirimleri uygularsınız. Aşağıdaki kod örneği, genel bir sınıfta bir ortak değişken arabiriminnasıl uygulanacağını gösterir.

```csharp
interface ICovariant<out R>
{
    R GetSomething();
}
class SampleImplementation<R> : ICovariant<R>
{
    public R GetSomething()
    {
        // Some code.
        return default(R);
    }
}
```

Varyant arabirimlerini uygulayan sınıflar değişmez. Örneğin, aşağıdaki kodu göz önünde bulundurun.

```csharp
// The interface is covariant.
ICovariant<Button> ibutton = new SampleImplementation<Button>();
ICovariant<Object> iobj = ibutton;

// The class is invariant.
SampleImplementation<Button> button = new SampleImplementation<Button>();
// The following statement generates a compiler error
// because classes are invariant.
// SampleImplementation<Object> obj = button;
```

## <a name="extending-variant-generic-interfaces"></a>Varyant Genel Arabirimlerini Genişletme

Bir varyant genel arabirimi genişletdiğinizde, `in` türetilen arabirimin varyansı destekleyip desteklemediğini açıkça belirtmek için anahtar kelimeleri ve `out` anahtar kelimeleri kullanmanız gerekir. Derleyici, genişletilmekte olan arabirimden varyans çıkarmıyor. Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

`IInvariant<T>` Arabirimde, genel tür `T` parametresi değişmez, `IExtCovariant<out T>` tür parametresi ise aynı arabirimde olsa da, tür parametresi birlikte değişmezdir. Aynı kural, karşıt genel tip parametrelere uygulanır.

Hem genel tür parametresinin `T` bir araya geldiği arabirimi hem de genişletme arabiriminde genel tür parametresi `T` değişmezse, karşıt olduğu arabirimi genişleten bir arabirim oluşturabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

Ancak, genel bir tür `T` parametresi tek bir arabirimde eşdeğişken olarak bildirilirse, bunu genişletme arabiriminde karşıt değişken olarak beyan edemezsiniz veya tam tersi. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a>Belirsizlikten Kaçınma

Varyant genel arabirimleri uyguladığınız zaman, varyans bazen belirsizliğe yol açabilir. Bu kaçınılmalıdır.

Örneğin, bir sınıfta farklı genel tür parametreleri ile aynı varyant genel arabirimi açıkça uygularsanız, belirsizlik oluşturabilirsiniz. Derleyici bu durumda bir hata üretmez, ancak çalışma zamanında hangi arabirim uygulamasının seçileceği belirtilmemiştir. Bu, kodunuzda ince hatalara yol açabilir. Aşağıdaki kod örneğini inceleyin.

```csharp
// Simple class hierarchy.
class Animal { }
class Cat : Animal { }
class Dog : Animal { }

// This class introduces ambiguity
// because IEnumerable<out T> is covariant.
class Pets : IEnumerable<Cat>, IEnumerable<Dog>
{
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()
    {
        Console.WriteLine("Cat");
        // Some code.
        return null;
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        // Some code.
        return null;
    }

    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()
    {
        Console.WriteLine("Dog");
        // Some code.
        return null;
    }
}
class Program
{
    public static void Test()
    {
        IEnumerable<Animal> pets = new Pets();
        pets.GetEnumerator();
    }
}
```

Bu örnekte, yöntemin `pets.GetEnumerator` ve `Cat` . `Dog` Bu, kodunuzda sorunlara neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)
- [Func ve Action Generic Delegeler için Varyans Kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)
