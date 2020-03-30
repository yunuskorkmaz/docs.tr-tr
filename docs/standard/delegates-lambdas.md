---
title: Temsilciler ve lambda ifadeleri
description: Temsilcilerin, doğrudan çağrılabilen veya başka bir yönteme geçirilebilen ve çağrılan belirli bir yöntem imzasını belirten bir türü nasıl tanımladığını öğrenin.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 34bfa4c6007ec771f784e927675f4e24d52e194f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391240"
---
# <a name="delegates-and-lambdas"></a>Temsilciler ve lambda ifadeleri

Temsilciler, belirli bir yöntem imzasını belirten bir tür tanımlar. Bu imzayı karşılayan bir yöntem (statik veya örnek) bu tür bir değişkene atanabilir, sonra doğrudan (uygun bağımsız değişkenlerle) çağrılabilir veya bağımsız değişkenin kendisi olarak başka bir yönteme aktarılabilir ve sonra çağrılabilir. Aşağıdaki örnek, temsilci kullanımını gösterir.

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* Satır `public delegate string Reverse(string s);` belirli bir imza bir temsilci türü oluşturur, bu durumda bir dize parametresi alır ve sonra bir dize parametresi döndürür bir yöntem.
* `static string ReverseString(string s)` Tanımlanan temsilci türüyle aynı imzaya sahip yöntem, temsilciyi uygular.
* Satır, `Reverse rev = ReverseString;` ilgili temsilci türünden bir değişkene bir yöntem atayabileceğinizi gösterir.
* Satır, `Console.WriteLine(rev("a string"));` temsilciyi çağırmak için temsilci türünden bir değişkenin nasıl kullanılacağını gösterir.

Geliştirme işlemini kolaylaştırmak için .NET, programcıların yeniden kullanabileceği ve yeni türler oluşturması gerekmeyen bir dizi temsilci türü içerir. Bunlar `Func<>` `Action<>` ,ve `Predicate<>`,, yeni temsilci türlerini tanımlamaya gerek kalmadan .NET API'leri boyunca çeşitli yerlerde kullanılabilirler. Tabii ki, çoğunlukla kullanılmak üzere olması gerekiyordu yolu ile ilgisi var onların imzaları göreceğiniz gibi üç arasında bazı farklılıklar vardır:

* `Action<>`temsilcinin bağımsız değişkenlerini kullanarak bir eylem gerçekleştirmeye ihtiyaç duyulduğunda kullanılır. Kapsüllediği yöntem bir değer döndürmez.
* `Func<>`genellikle elinizde bir dönüşüm olduğunda, yani temsilcinin bağımsız değişkenlerini farklı bir sonuca dönüştürmeniz gerekir. Projeksiyonlar bunun en önemli örneklerindendir. Kapsülletiyi kapaya saran yöntem belirli bir değeri döndürür.
* `Predicate<>`bağımsız değişkenin temsilcinin durumunu karşılar mı belirlemeniz gerektiğinde kullanılır. Aynı zamanda bir `Func<T, bool>`, yöntem bir boolean değeri döndürür anlamına gelir olarak yazılabilir.

Şimdi yukarıdaki örneği alabilir ve özel bir `Func<>` tür yerine temsilci kullanarak yeniden yazabilirsiniz. Program tam olarak aynı çalışmaya devam edecektir.

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

Bu basit örnek için, `Main` yöntem dışında tanımlanan bir yöntem olması biraz gereksiz görünüyor. Bu nedenle .NET Framework 2.0 **anonim delegeler**kavramını tanıttı. Onların desteği ile herhangi bir ek tür veya yöntem belirtmenize gerek kalmadan "satır" temsilcileri oluşturabilirsiniz. Yalnızca gerektiğinde temsilcinin tanımını satır alabilirsiniz.

Örneğin, değiştirip anonim temsilcimizi kullanarak yalnızca çift sayıların listesini filtreleyip konsola yazdıracağız.

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

Gördüğünüz gibi, temsilcinin gövdesi diğer temsilciler gibi yalnızca bir dizi ifadedir. Ama bunun ayrı bir tanım olması yerine, _ad hoc_ <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> bu yönteme yaptığımız çağrıda geçici olarak tanıttık.

Ancak, bu yaklaşım bile, hala biz atabilir çok kod var. Lambda **ifadeleri** burada devreye giriyor.

Lambda ifadeler, ya da kısaca sadece "lambdas", C # 3.0 ilk tanıtıldı, Dil Entegre Sorgu (LINQ) temel yapı taşlarından biri olarak. Onlar sadece temsilcileri kullanmak için daha uygun bir sözdizimi vardır. Bir imza ve yöntem gövdesi beyan ederler, ancak bir temsilciye atanmadıkça kendilerine ait resmi bir kimlikleri yoktur. Temsilcilerin aksine, doğrudan olay kaydının sol tarafı olarak veya çeşitli LINQ yan tümceleri ve yöntemleri yle atanabilirler.

Lambda ifadesi bir temsilci belirtmenin başka bir yolu olduğundan, yukarıdaki örneği anonim bir temsilci yerine lambda ifadesini kullanmak için yeniden yazabilmek gerekir.

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

Önceki örnekte kullanılan lambda ifadesidir. `i => i % 2 == 0` Yine, bu delegeleri kullanmak için **sadece çok** uygun bir sözdizimi, bu nedenle kapakları altında ne olur anonim temsilci ile ne benzer.

Yine, lambdas sadece delegeler, hangi herhangi bir sorun olmadan bir olay işleyiciolarak kullanılabilir anlamına gelir, aşağıdaki kod snippet gösterdiği gibi.

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

Bu `+=` bağlamda işleç bir [olaya](../../docs/csharp/language-reference/keywords/event.md)abone olmak için kullanılır. Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

## <a name="further-reading-and-resources"></a>Daha fazla okuma ve kaynaklar

* [Temsilciler](../../docs/csharp/programming-guide/delegates/index.md)
* [Anonim Fonksiyonlar](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Lambda ifadeleri](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
