---
title: Değişken genel arabirimler oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: d8e7e8a59aeff27531187e5171a76651440ffc4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526913"
---
# <a name="creating-variant-generic-interfaces-c"></a>Değişken genel arabirimler oluşturma (C#)
Genel Tür parametrelerine birlikte değişken olarak arabirimleri bildirebilir veya değişken karşıtı. *Kovaryans* dönüş türleri genel tür parametreleri tarafından tanımlanan değerinden daha fazla türetilmiş arabirim yöntemleri sağlar. *Kontravaryans* genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri arabirim yöntemleri sağlar. Birlikte değişken olan genel bir arabirim veya değişken karşıtı genel tür parametreleri çağrılır *değişken*.  
  
> [!NOTE]
>  .NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur. .NET Framework'teki değişken arabirimler listesi için bkz. [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Bildirim değişken genel arabirimler  
 Değişken genel arabirimler kullanarak bildirebilirsiniz `in` ve `out` genel tür parametreleri için anahtar sözcükler.  
  
> [!IMPORTANT]
>  `ref`, `in`, ve `out` C# parametrelerinde değişken olamaz. Değer türleri varyansı da desteklemez.  
  
 Genel tür parametresi birlikte değişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Birlikte değişen türde aşağıdaki koşulları karşılaması gerekir:  
  
-   Türü yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız bir türü olarak kullanılmaz. Bu, aşağıdaki örnekte gösterilmiştir türü `R` birlikte değişken olarak bildirilir.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     Bu kuralın tek istisnası yoktur. Bir yöntem parametresi olarak bir değişken karşıtı Genel temsilci varsa, türü için temsilci genel tür parametre olarak kullanabilirsiniz. Bu tür tarafından gösterilmiştir `R` aşağıdaki örnekte. Daha fazla bilgi için [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   Türü genel kısıtlama olarak arabirim yöntemleri için kullanılmaz. Bu, aşağıdaki kodda gösterilmiştir.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 Bir genel tür parametresi değişken karşıtı kullanarak bildirebilirsiniz `in` anahtar sözcüğü. Değişken karşıtı türü arabirim yöntemleri dönüş türü olarak değil de yalnızca bir tür yöntem bağımsız olarak kullanılabilir. Değişken karşıtı türü genel kısıtlamalar için de kullanılabilir. Aşağıdaki kod, bir değişken karşıtı arabirimi bildirme ve bir genel kısıtlama yöntemlerinden biri için kullanma gösterilmektedir.  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 Ayrıca aşağıdaki kod örneğinde gösterildiği gibi aynı arabirimi, ancak farklı türde parametreler için hem Kovaryans ve kontravaryans desteklemek mümkündür.  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Değişken genel arabirimler uygulama  
 Değişken genel arabirimler sınıflarda sabit arabirimler için kullanılan aynı sözdizimini kullanarak uygulayın. Aşağıdaki kod örneği, birlikte değişken arabirimi genel bir sınıf uygulamak gösterilmektedir.  
  
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
  
 Sabit değişken arabirimleri uygulayan sınıflar. Örneğin, aşağıdaki kodu düşünün.  
  
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
  
## <a name="extending-variant-generic-interfaces"></a>Genişletme değişken genel arabirimler  
 Bir değişken genel arabirim genişlettiğinizde kullanmak zorunda `in` ve `out` açıkça türetilmiş bir arabirim varyansı destekleyip desteklemediğini belirlemek için anahtar sözcükler. Derleyici, varyans Genişletilmekte olan arabiriminden Infer değil. Örneğin, aşağıdaki arabirimlerinden göz önünde bulundurun.  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 İçinde `IInvariant<T>` arabirim, genel tür parametresi `T` değişmezdir, ise içinde `IExtCovariant<out T>` hem arabirimleri aynı arabirimi genişletmek rağmen tür parametresi değişkendir. Aynı kural, değişken karşıtı genel tür parametreleri için uygulanır.  
  
 Burada, genel tür parametresi her iki arabirimini genişletir bir arabirim oluşturabilirsiniz `T` birlikte değişkendir ve genel tür parametresi, genişletme, değişken karşıtı olduğu arabirimi arabirim `T` değişmezdir. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 Ancak, genel tür parametresi, `T` olan tek bir arabirimde bildirilen değişken, değişken karşıtı bildirip genişletme arabiriminde veya tam tersi. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a>Belirsizlik kaçınma  
 Değişken genel arabirimler uyguladığınızda, varyans bazen için karışıklığa neden olabilir. Bu kaçınılmalıdır.  
  
 Örneğin, bir sınıf içinde farklı bir genel tür parametreleri ile aynı değişken genel arabirim açıkça uygularsanız, belirsizlik oluşturabilirsiniz. Derleyici bu durumda bir hata oluşturmaz, ancak çalışma zamanında hangi arabirim uygulaması seçilir belirtilmedi. Bu küçük hatalar, kodunuzda neden olabilir. Aşağıdaki kod örneği göz önünde bulundurun.  
  
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
  
 Bu örnekte, belirtilmeyen nasıl `pets.GetEnumerator` ücretlerinin arasında `Cat` ve `Dog`. Kodunuzda bu sorunlara neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
- [İşlev ve eylem genel temsilcileri (C#) için varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
