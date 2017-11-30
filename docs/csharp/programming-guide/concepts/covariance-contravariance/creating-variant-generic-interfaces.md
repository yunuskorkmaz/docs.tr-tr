---
title: "Değişken genel arabirimler oluşturma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0a6ba6bd85d0bdfa7e98dd85886fee89527b59fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-variant-generic-interfaces-c"></a>Değişken genel arabirimler oluşturma (C#)
Genel tür parametreleri eşdeğişken olarak arabirimlerdeki bildirebilir veya karşıtı. *Kovaryans* dönüş türleri genel tür parametreleri tarafından tanımlanan daha fazla türetilmiş arabirim yöntemleri sağlar. *Değişken karşıtı* genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri arabirim yöntemleri sağlar. Eşdeğişken sahip genel arabirim veya karşıtı genel tür parametreleri çağrılır *değişken*.  
  
> [!NOTE]
>  .NET framework 4 birkaç mevcut genel arabirimler sapma desteği sunmuştur. .NET Framework'teki değişken arabirimler listesi için bkz: [genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Bildiren değişken genel arabirimler  
 Değişken genel arabirimler kullanarak bildirebilirsiniz `in` ve `out` genel tür parametreleri için anahtar sözcükler.  
  
> [!IMPORTANT]
>  `ref`ve `out` parametreleri C# değişken olamaz. Türlerin varyans da desteklemez.  
  
 Genel tür parametresi eşdeğişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Eşdeğişken türü aşağıdaki koşulları karşılaması gerekir:  
  
-   Türü yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız değişkenleri bir tür olarak kullanılmaz. Bu, aşağıdaki örnekte gösterilmiştir türü `R` eşdeğişken bildirilir.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     Bu kural için bir istisna vardır. Karşıtı Genel temsilci bir yöntem parametresi olarak varsa, türü için temsilci genel tür parametresi olarak kullanabilirsiniz. Bu türü tarafından gösterilen `R` aşağıdaki örnekte. Daha fazla bilgi için bkz: [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilciler (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   Türü, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz. Bu aşağıdaki kodda gösterilmiştir.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 Genel tür parametresi karşıtı kullanarak bildirebilirsiniz `in` anahtar sözcüğü. Karşıtı türü arabirim yöntemleri dönüş türü olarak değil de yalnızca yöntem bağımsız değişkenleri bir tür olarak kullanılabilir. Karşıtı türü, genel kısıtlamalar için de kullanılabilir. Aşağıdaki kod karşıtı arabirimi bildirin ve genel bir kısıtlama yöntemlerinden biri için nasıl kullanılacağını gösterir.  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 Ayrıca aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri yanı sıra, aynı arabiriminde Kovaryans ve kontravaryans desteklemek mümkündür.  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Uygulama değişken genel arabirimler  
 Değişken genel arabirimler değişmez arabirimleri için kullanılan aynı sözdizimini kullanarak sınıflarda uygulayın. Aşağıdaki kod örneğinde, genel bir sınıf bir eşdeğişken arabirimini uygulayan gösterilmektedir.  
  
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
  
 Değişken arabirimler uygulayan sınıflar değişmez. Örneğin, aşağıdaki kodu göz önünde bulundurun.  
  
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
 Değişken genel bir arabirim genişlettiğinizde kullanmak zorunda `in` ve `out` açıkça türetilmiş bir arabirim farkı destekleyip desteklemediğini belirlemek için anahtar sözcükler. Derleyici genişletilen arabiriminden varyansı Infer değil. Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 İçinde `IInvariant<T>` arabirim, genel tür parametresi `T` değişmez, olan ancak içinde `IExtCovariant<out T>` aynı arabirimi her iki arabirimde genişletmek rağmen tür parametresi değişkendir. Aynı kural karşıtı genel tür parametreleri için uygulanır.  
  
 Genel parametre girildiği iki arabirim genişleten bir arabirim oluşturabilirsiniz `T` değişkendir ve varsa genişletme içinde karşıtı olduğu arabirimi arabirim genel tür parametresi `T` sabit değil. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 Ancak, genel türde bir parametre değilse `T` olan bir arabiriminde eşdeğişken bildirilen, siz onu karşıtı bildiremezsiniz genişletme arabiriminde veya tersi. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a>Belirsizliği önleme  
 Değişken genel arabirimler uyguladığınızda farkı bazen belirsizlik için yol açabilir. Bu kaçınılmalıdır.  
  
 Örneğin, bir sınıf tarafından açıkça farklı genel tür parametreleri ile aynı değişken genel arabirim uygularsanız, belirsizlik oluşturabilirsiniz. Derleyici bir hata bu durumda üretmez, ancak çalışma zamanında hangi arabirim uygulamasına seçilir belirtilmedi. Bu, kodunuzda Zarif hataları neden olabilir. Aşağıdaki kod örneği göz önünde bulundurun.  
  
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
  
 Bu örnekte, belirtilmeyen nasıl `pets.GetEnumerator` ücretlerinin arasında `Cat` ve `Dog`. Bu, kodunuzda sorunlara neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [İşlev ve eylem genel temsilciler (C#) için varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
