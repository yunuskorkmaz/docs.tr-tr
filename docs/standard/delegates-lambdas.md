---
title: Temsilciler ve lambda ifadeleri
description: Temsilcilerin, doğrudan çağrılabilen veya başka bir yönteme geçirilebilen ya da çağrılan belirli bir yöntem imzasını belirten bir türü nasıl tanımladığını öğrenin.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 0abcc73e31eab89c422513acf778bc8bd092e788
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345546"
---
# <a name="delegates-and-lambdas"></a>Temsilciler ve lambda ifadeleri

Temsilciler, belirli bir yöntem imzasını belirten bir tür tanımlar. Bu imzayı karşılayan bir Yöntem (statik veya örnek), bu tür bir değişkene atanabilir, daha sonra doğrudan (uygun bağımsız değişkenlerle) veya bağımsız değişken olarak başka bir yönteme geçirilir ve ardından çağırılır. Aşağıdaki örnek, temsilci kullanımını gösterir.

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

* `public delegate string Reverse(string s);` satırı belirli bir imzanın temsilci türünü oluşturur, bu durumda bir dize parametresi alan ve sonra bir dize parametresi döndüren bir yöntem.
* Tanımlı temsilci türüyle tam olarak aynı imzaya sahip `static string ReverseString(string s)` yöntemi, temsilciyi uygular.
* `Reverse rev = ReverseString;` satırı, karşılık gelen temsilci türünün bir değişkenine bir yöntem atayacağınızı gösterir.
* `Console.WriteLine(rev("a string"));` satırı, temsilciyi çağırmak için bir temsilci türü değişkeninin nasıl kullanılacağını gösterir.

Geliştirme sürecini kolaylaştırmak için, .NET, programcıların yeniden kullanılabilen ve yeni türler oluşturmak zorunda olmayan bir temsilci türleri kümesi içerir. Bunlar `Func<>`, `Action<>` ve `Predicate<>`ve yeni temsilci türleri tanımlamaya gerek kalmadan .NET API 'Lerinde çeşitli yerlerde kullanılabilirler. Kuşkusuz, her ikisi arasında, genellikle kullanılması amaçlanan gibi olması gereken üç farklı bir farklılık vardır:

* `Action<>`, temsilcinin bağımsız değişkenlerini kullanarak bir eylem gerçekleştirmeniz gerektiğinde kullanılır.
* `Func<>`, genellikle bir dönüşüme sahip olduğunuzda kullanılır, diğer bir deyişle, temsilcinin bağımsız değişkenlerini farklı bir sonuca dönüştürmeniz gerekir. Tahminler bunun ana örneğidir.
* `Predicate<>`, bağımsız değişkenin temsilci koşulunu karşılayıp karşılamadığını belirlemeniz gerektiğinde kullanılır. Ayrıca, bir `Func<T, bool>`olarak yazılabilir.

Şimdi örneğimizi alıp özel bir tür yerine `Func<>` temsilcisini kullanarak yeniden yazabilirsiniz. Program tamamen aynı çalışmaya devam edecektir.

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

Bu basit örnek için `Main` yöntemi dışında tanımlanan bir yöntemin olması biraz daha fazla görünüyor. Bunun nedeni 2,0 .NET Framework **anonim temsilciler**kavramını sunmuştur. Desteğiyle, ek bir tür veya yöntem belirtmek zorunda kalmadan "satır içi" Temsilciler oluşturabilirsiniz. İhtiyaç duyduğunuz temsilcinin tanımını yalnızca satır içi olarak alırsınız.

Bir örnek için, bu anahtarı değiştirmek ve anonim temsilcimizi kullanarak tek hatta sayıların bir listesini filtreleyeceğiz ve ardından konsola yazdıracağız.

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

Gördüğünüz gibi, temsilcinin gövdesi, diğer tüm temsilciler gibi yalnızca bir ifade kümesidir. Ancak, ayrı bir tanım olmak yerine, <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metoduna yapılan Çağrımızda BT _geçici_ olarak tanıtıldık.

Ancak, bu yaklaşımda bile, fırladığımız çok fazla kod vardır. Bu, **lambda ifadelerinin** oynatma içine geldiği yerdir.

Lambda ifadeleri veya Short için yalnızca "Lambdalar", dil ile tümleşik sorgu C# (LINQ) temel yapı taşlarından biri olarak 3,0 ' de ilk sunulmuştur. Temsilciler kullanmanın yalnızca daha uygun bir sözdizimi vardır. Bir temsilciye atanmadıkları takdirde, bir imza ve Yöntem gövdesi bildirir, ancak kendi biçimsel kimliği yoktur. Temsilcilerden farklı olarak, doğrudan olay kaydının sol tarafı olarak veya çeşitli LINQ yan tümceleri ve yöntemleri olarak atanabilir.

Lambda ifadesi bir temsilci belirtmenin yalnızca başka bir yolu olduğundan, yukarıdaki örneği anonim bir temsilci yerine bir lambda ifadesi kullanacak şekilde yeniden yazamayacak.

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

Yukarıdaki örnekte, kullanılan lambda ifadesi `i => i % 2 == 0`. Bu, temsilcileri kullanmak için **oldukça** kullanışlı bir sözdizimidir, bu nedenle, kapsamaları altında olduğu gibi, anonim temsilciyle ne gibi bir durumla benzerdir.

Daha sonra Lambdalar yalnızca temsilcidir. Bu, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir sorun olmadan bir olay işleyicisi olarak kullanılabilecekleri anlamına gelir.

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

Bu bağlamdaki `+=` işleci bir [olaya](../../docs/csharp/language-reference/keywords/event.md)abone olmak için kullanılır. Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Daha fazla okuma ve kaynak

* [Temsilciler](../../docs/csharp/programming-guide/delegates/index.md)
* [Anonim İşlevler](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Lambda ifadeleri](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
