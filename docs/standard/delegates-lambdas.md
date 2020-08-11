---
title: Temsilciler ve lambda ifadeleri
description: Belirli bir yöntem imzasını belirten bir türü tanımlayan temsilcilerin doğrudan veya başka bir yönteme geçip çağrılabilecek bir tür tanımlar.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 1307599a3832be5f48cd62a7b8c1be7f76a3d4a5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063750"
---
# <a name="delegates-and-lambdas"></a>Temsilciler ve lambda ifadeleri

Temsilciler belirli bir yöntem imzasını belirten bir tür tanımlar. Bu imzayı karşılayan bir Yöntem (statik veya örnek), bu tür bir değişkene atanabilir, daha sonra doğrudan (uygun bağımsız değişkenlerle) veya bağımsız değişken olarak başka bir yönteme geçirilir ve ardından çağırılır. Aşağıdaki örnek, temsilci kullanımını gösterir.

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

* `public delegate string Reverse(string s);`Satır, bu durumda bir dize parametresi alan ve sonra bir dize parametresi döndüren bir yöntem olan belirli bir imzanın temsilci türünü oluşturur.
* `static string ReverseString(string s)`Tanımlı temsilci türüyle tam olarak aynı imzaya sahip olan yöntemi temsilciyi uygular.
* `Reverse rev = ReverseString;`Satırı, karşılık gelen temsilci türünün bir değişkenine bir yöntem atayacağınızı gösterir.
* `Console.WriteLine(rev("a string"));`Satır, temsilciyi çağırmak için bir temsilci türü değişkeninin nasıl kullanılacağını gösterir.

Geliştirme sürecini kolaylaştırmak için, .NET, programcıların yeniden kullanılabilen ve yeni türler oluşturmak zorunda olmayan bir temsilci türleri kümesi içerir. Bu türler `Func<>` , `Action<>` ve ' dir `Predicate<>` ve yeni temsilci türleri tanımlamak zorunda kalmadan kullanılabilirler. Üç tür arasında, kullanılması amaçlanan şekilde yapılacak bazı farklılıklar vardır:

* `Action<>`Temsilcinin bağımsız değişkenlerini kullanarak bir eylem gerçekleştirmeniz gerektiğinde kullanılır. Kapsülleyen Yöntem bir değer döndürmez.
* `Func<>`genellikle bir dönüşüme sahip olduğunuzda kullanılır, diğer bir deyişle, temsilcinin bağımsız değişkenlerini farklı bir sonuca dönüştürmeniz gerekir. Tahminler iyi bir örnektir. Kapsülleyen yöntemi belirtilen değeri döndürür.
* `Predicate<>`bağımsız değişkenin temsilcinin koşulunu karşılayıp karşılamadığını belirlemeniz gerektiğinde kullanılır. Ayrıca bir olarak yazılabilir, bu da `Func<T, bool>` yöntemin bir Boolean değer döndürdüğü anlamına gelir.

Şimdi örneğimizi alıp `Func<>` özel bir tür yerine temsilciyi kullanarak yeniden yazabilirsiniz. Program tamamen aynı çalışmaya devam edecektir.

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

Bu basit örnek için yöntemin dışında tanımlanmış bir yöntemin olması biraz daha fazla `Main` görünüyor. .NET Framework 2,0 *anonim temsilciler*kavramını ortaya sunmuştur, bu da ek bir tür veya yöntem belirtmeye gerek kalmadan "satır içi" Temsilciler oluşturmanızı sağlar.

Aşağıdaki örnekte, anonim bir temsilci bir listeyi yalnızca çift sayılarla filtreleyerek konsola yazdırır.

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

Gördüğünüz gibi, temsilcinin gövdesi, diğer tüm temsilciler gibi yalnızca bir ifade kümesidir. Ancak, ayrı bir tanım olmak yerine, yönteme yönelik Çağrımızda bir _ad_ tanıdık <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> .

Ancak, bu yaklaşımda bile, fırladığımız çok fazla kod vardır. Bu, *lambda ifadelerinin* oynatma içine geldiği yerdir. Lambda ifadeleri veya Short için yalnızca "Lambdalar", dil ile tümleşik sorgu (LINQ) temel yapı taşlarından biri olarak C# 3,0 ' de tanıtılmıştı. Temsilciler kullanmanın yalnızca daha uygun bir sözdizimi vardır. Bir temsilciye atanmadıkları takdirde, bir imza ve Yöntem gövdesi bildirir, ancak kendi biçimsel kimliği yoktur. Temsilcilerden farklı olarak, doğrudan olay kaydının sağ tarafı olarak veya çeşitli LINQ yan tümceleri ve yöntemleri olarak atanabilir.

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

Yukarıdaki örnekte, kullanılan lambda ifadesi `i => i % 2 == 0` . Ayrıca, temsilcileri kullanmak için kullanışlı bir sözdizimidir. Kapakların altında ne olacağı, anonim temsilciyle ilgili olana benzerdir.

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

`+=`Bu bağlamdaki işleç bir [olaya](../csharp/language-reference/keywords/event.md)abone olmak için kullanılır. Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Daha fazla okuma ve kaynak

* [Temsilciler](../csharp/programming-guide/delegates/index.md)
* [Anonim Işlevler](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Lambda ifadeleri](../csharp/language-reference/operators/lambda-expressions.md)
