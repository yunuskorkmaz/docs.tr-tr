---
title: Temsilciler ve lambda ifadeleri
description: Nasıl doğrudan veya başka bir yönteme ve adlı bir özel yöntem imzası belirtmek Temsilciler, tür tanımlama hakkında bilgi edinin.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 3d4aa5e60ab9bb134716bddcf90b6fc6b07c2ea0
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656160"
---
# <a name="delegates-and-lambdas"></a>Temsilciler ve lambda ifadeleri

Temsilciler belirli yöntem imzası belirtmek tanımlayan bir tür. Bir yöntem (statik veya örnek) Bu imza Bu türden bir değişkene atanabilir sonra doğrudan (uygun bağımsız değişkenlerle) olarak adlandırılan veya bağımsız değişken olarak kendisini başka bir yönteme geçirilen ve ardından adlı karşılar. Aşağıdaki örnekte, temsilci kullanımını gösterir.

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

* `public delegate string Reverse(string s);` Satırı bu durumda bir temsilci türü belirli imzası, bir dize parametresi alan ve sonra bir dize parametresi döndüren bir yöntem oluşturur.
* `static string ReverseString(string s)` Tanımlı temsilci türüyle tam aynı imzaya sahip yöntemi temsilci uygular.
* `Reverse rev = ReverseString;` Satır gösterir bir yöntemi karşılık gelen temsilci türünün bir değişkene atayabilirsiniz.
* `Console.WriteLine(rev("a string"));` Satırı bir temsilci türünde bir değişken temsilci çağırmak için nasıl kullanılacağını gösterir.

Geliştirme işlemi kolaylaştırmak için .NET programcıları yeniden ve yeni türler oluşturmak için olmaması temsilci türleri kümesi içerir. Bunlar `Func<>`, `Action<>` ve `Predicate<>`, ve bunlar gerek kalmadan .NET API'lerini çeşitli yerlerde yeni temsilci türleri tanımlamak için kullanılabilir. Elbette, kullanılacak düşünülen işlemleriyle yapmak için çoğunlukla sahip imzaları içindeki göreceğiniz gibi üç arasında bazı farklar vardır:

*   `Action<>` temsilcinin bağımsız değişkenleri kullanarak bir eylem gerçekleştirmek için ihtiyaç olduğunda kullanılır.
*   `Func<>` genellikle bir dönüştürme taraftan, varsa, kullanılan diğer bir deyişle, temsilcinin bağımsız değişkenleri farklı bir sonuç biçimine dönüştürmeniz gerekir. Tahminler, bu birinci bir örnektir.
*   `Predicate<>` bağımsız değişken, temsilci koşulu karşılayıp karşılamadığını belirlemek gerektiğinde kullanılır. Olarak da yazılabilir bir `Func<T, bool>`.

Biz artık yukarıdaki örneğimizde alabilir ve kullanarak yeniden `Func<>` temsilci yerine özel bir tür. Program, tam olarak aynı çalışmaya devam edecek.

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

Bu basit örnekte, olması dışında tanımlanmış bir yöntem `Main` yöntemi biraz gereksiz görünüyor. .NET Framework 2.0 sunulan kavramı, bu nedenle olan **anonim Temsilciler**. Destek ile herhangi bir ek türü veya yöntemini belirtmek zorunda kalmadan "satır içi" temsilci oluşturmak kullanabilirsiniz. Yalnızca satır gerek duyduğunuz, temsilci tanımı.

Örneğin, yedekleme geçin ve yalnızca çift sayıların bir listeyi filtreleyin ve ardından bunları konsola yazdırır bizim anonim temsilci kullanmak için kullanacağız.

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

Gördüğünüz gibi temsilci yalnızca bir dizi ifadeleri, herhangi bir temsilci gövdesidir. Ancak bunun yerine ayrı bir tanımı olan, onu tanıttık _geçici_ bizim çağrıda <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> yöntemi.

Ancak, bile bu yaklaşımda, yine de biz hemen oluşturabilecek kadar kodu yok. Burada **lambda ifadeleri** oyuna gelir.

Lambda ifadeleri veya kısaca, yalnızca "lambdalar" de kullanıma sunulmuştur ilk C# 3.0, temel yapı taşlarını, dil tümleşik sorgu (LINQ) biri olarak. Temsilcileri kullanma için yalnızca bir daha kullanışlı söz dizimi değildirler. Bir imza ve bir yöntem gövdesi bildirmek, ancak bir temsilciye atanmış oldukları sürece, kendi, biçimsel bir kimlik yok. Temsilciler, bunlar doğrudan sol tarafı olay kaydı veya çeşitli LINQ yan tümceleri ve yöntemler olarak atanabilir.

Bir lambda ifadesi bir temsilci belirtmenin başka bir yol olduğundan, biz bir anonim temsilci yerine bir lambda ifadesi kullanmak için yukarıdaki örnek yeniden mümkün olması gerekir.

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

Önceki örnekte kullanılan lambda ifadesidir `i => i % 2 == 0`. Yeniden yalnızca olduğu bir **çok** ne olacağını perde anonim temsilci ile neler için benzer şekilde, temsilciler kullanılarak için kullanışlı bir söz dizimi.

Yine, lambda ifadeleri, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir sorun olmadan bir olay işleyicisi olarak kullanılabilir anlamına gelir yalnızca temsilcileri.

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

`+=` İşleci bu bağlamda abone olmak için kullanılan bir [olay](../../docs/csharp/language-reference/keywords/event.md). Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Daha fazla bilgi ve kaynaklar

*   [Temsilciler](../../docs/csharp/programming-guide/delegates/index.md)
*   [Anonim İşlevler](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [Lambda ifadeleri](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
