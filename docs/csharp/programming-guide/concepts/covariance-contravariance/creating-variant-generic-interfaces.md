---
title: Değişken genel arabirimler (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595312"
---
# <a name="creating-variant-generic-interfaces-c"></a>Değişken genel arabirimler (C#) oluşturma

Arabirimlerdeki genel tür parametrelerini birlikte değişken veya değişken karşıtı olarak bildirebilirsiniz. *Kovaryans* , Arabirim yöntemlerinin genel tür parametreleri tarafından tanımlananla daha fazla türetilmiş dönüş türüne sahip olmasına izin verir. *Değişken varyans* , Arabirim yöntemlerinin genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasına olanak sağlar. Değişkenle birlikte değişken veya değişken karşıtı genel tür parametrelerine sahip genel bir arabirim *değişken*olarak adlandırılır.

> [!NOTE]
> .NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir. .NET Framework değişken arabirimlerinin listesi için bkz. [Genel Arabirimlerde VaryansC#()](./variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>VARIANT genel arabirimlerini bildirme

Genel tür parametreleri için `in` ve `out` anahtar sözcüklerini kullanarak VARIANT genel arabirimleri bildirebilirsiniz.

> [!IMPORTANT]
> `ref`, `in`ve `out` içindeki C# parametreleri varyant olamaz. Değer türleri de varyansı desteklemez.

`out` Anahtar sözcüğünü kullanarak genel tür parametresi ortak değişkeni bildirebilirsiniz. Covaryant türü şu koşulları karşılamalıdır:

- Tür, yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz. Bu, türünün `R` birlikte değişken olarak bildirildiği aşağıdaki örnekte gösterilmiştir.

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    Bu kural için bir özel durum var. Bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, türü temsilci için genel bir tür parametresi olarak kullanabilirsiniz. Bu, aşağıdaki örnekteki tür `R` tarafından gösterilmiştir. Daha fazla bilgi için bkz. [temsilcilerin içindeki varyansC#()](./variance-in-delegates.md) ve [Func ve ACTION Genel Temsilciler (C#) için varyans kullanma](./using-variance-for-func-and-action-generic-delegates.md).

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

`in` Anahtar sözcüğünü kullanarak genel tür parametresi değişken karşıtı bildirebilirsiniz. Değişken karşıtı türü, Arabirim yöntemlerinin dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir. Değişken karşıtı türü, genel kısıtlamalar için de kullanılabilir. Aşağıdaki kod, bir değişken karşıtı arabirimin nasıl bildirilemeyeceğini ve yöntemlerinden biri için genel bir kısıtlama nasıl kullanıldığını gösterir.

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

Ayrıca, aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri için aynı arabirimdeki kovaryansı ve değişken varyansı desteklemek de mümkündür.

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a>VARIANT genel arabirimlerini uygulama

Sabit arabirimler için kullanılan söz dizimini kullanarak sınıflarda VARIANT genel arabirimler uygulayabilirsiniz. Aşağıdaki kod örneği, bir genel sınıfta birlikte değişken arabiriminin nasıl uygulanacağını gösterir.

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

Varyant arabirimlerini uygulayan sınıflar sabit. Örneğin, aşağıdaki kodu göz önünde bulundurun.

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

## <a name="extending-variant-generic-interfaces"></a>VARIANT genel arabirimlerini genişletme

Bir varyant genel arabirimini genişlettiğinizde, türetilmiş arabirimin varyansı destekleyip desteklemediğini açıkça belirtmek `in` için `out` ve anahtar sözcüklerini kullanmanız gerekir. Derleyici, genişletilmekte olan arabirimden varyansı çıkarmıyor. Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

Arabirimde, genel tür parametresi `T` değişmez, `IExtCovariant<out T>` ancak her iki arabirim de aynı arabirimi genişletse de, tür parametresinde birlikte değişken olur. `IInvariant<T>` Aynı kural, değişken karşıtı genel tür parametrelerine uygulanır.

Hem genel tür parametresinin `T` birlikte değişken olduğu arabirimi hem de genişletme arabiriminde genel tür parametresi `T` sabit ise değişken karşıtı olan arabirimi genişleten bir arabirim oluşturabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

Ancak, bir genel tür parametresi `T` bir arabirimde birlikte değişken olarak bildirilirse, genişletme arabiriminde bu değişken karşıtı olarak bildiremezsiniz veya tam tersi de geçerlidir. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a>Belirsizlik önleme

VARIANT genel arabirimleri uyguladığınızda, fark bazen belirsizliğe neden olabilir. Bunun kaçınılması gerekir.

Örneğin, tek bir sınıfta farklı genel tür parametreleriyle aynı Varyant genel arabirimini açıkça uygularsanız, belirsizlik oluşturabilir. Derleyici bu durumda bir hata oluşturmaz, ancak çalışma zamanında hangi arabirim uygulamasının seçilme belirtilecektir. Bu, kodunuzda hafif hatalara neden olabilir. Aşağıdaki kod örneğini göz önünde bulundurun.

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

Bu örnekte, `pets.GetEnumerator` yönteminin ve `Dog`arasında `Cat` nasıl seçtiği belirtilmemiş. Bu, kodunuzda sorun oluşmasına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)
- [Func ve eylem genel temsilcileri için varyans kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)
