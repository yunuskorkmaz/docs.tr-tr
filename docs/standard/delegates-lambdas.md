---
title: Temsilciler ve lambdas
description: Nasıl doğrudan adlı veya başka bir yönteme geçirilen ve olarak adlandırılan belirli yöntem imzası belirtmek Temsilciler, tür tanımlama öğrenin.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: f8184b87fc62f378fe72138733f87de924da60f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574572"
---
# <a name="delegates-and-lambdas"></a>Temsilciler ve lambdas

Temsilciler belirli yöntem imzası belirtmek bir türünü tanımlayın. Bir yöntem (statik veya örnek) karşılayan bu imza Bu tür bir değişkene atanabilir sonra doğrudan (uygun bağımsız değişkenler ile) olarak adlandırılan veya bağımsız değişken olarak kendisi başka bir yönteme geçirilen ve sonra çağrılır. Aşağıdaki örnek temsilci kullanımını gösterir.

```csharp
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

*   Belirli bir imza bir temsilci türü oluşturuyoruz 4 satırında, bu durumda bir yöntemi, bir dize parametresi alan ve sonra bir dize parametresi döndürür.
*   6. satırda temsilci uyarlamasını tam aynı imzaya sahip bir yöntem sağlayarak tanımlarız.
*   13 satırında, uyumlu bir türü yöntemi atandığı `Reverse` temsilci.
*   Son olarak, 15 satırda bir dize tersine geçirme temsilci biz çağırır.

Geliştirme işlemini kolaylaştırmak için .NET programcıları yeniden kullanmak ve yeni türleri oluşturmak zorunda kalmazsınız temsilci türleri kümesi içerir. Bunlar `Func<>`, `Action<>` ve `Predicate<>`, ve bunlar içinde çeşitli yerlerde .NET API'lerini gerek kalmadan yeni temsilci türleri tanımlamak için kullanılabilir. Elbette, çoğunlukla kullanılacak demek yolu ile yapmak zorunda kendi imzaları de göreceğiniz gibi üç arasındaki bazı farklar vardır:

*   `Action<>` Temsilci bağımsız değişkenleri kullanarak bir eylem gerçekleştirmek üzere gereksinimi olduğunda kullanılır.
*   `Func<>` genellikle bir dönüşüm taraftan, varsa, kullanılan diğer bir deyişle, temsilci bağımsız farklı bir sonuç dönüştürme gerekir. Bu prime örneği projeksiyonlardır.
*   `Predicate<>` bağımsız değişken temsilci koşulu karşılayan varsa belirlemek üzere gerektiğinde kullanılır. Olarak da yazılabilir bir `Func<T, bool>`.

Biz şimdi örneğimizde yukarıdaki alabilir ve kullanarak yeniden `Func<>` temsilci yerine özel bir tür. Program, tam olarak aynı çalışmaya devam edecek.

```csharp
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

Bu basit örnekte, Main() yönteminin dışında tanımlanmış bir yöntemi olması biraz gereksiz gibi görünüyor. .NET Framework 2.0 kavramı sunulan bu nedenle olan **anonim Temsilciler**. Destek ile herhangi bir ek türü veya yöntemi belirtmek zorunda kalmadan "satır içi" Temsilciler oluşturabilirsiniz. Yalnızca ihtiyaç duyacağınız, temsilci tanımını satır içi.

Örneğin, biz yukarı geçin ve yalnızca çift sayı listesini filtrelemek ve bunları konsola yazdırma için anonim bizim temsilci kullanın alınacaktır.

```csharp
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
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

Vurgulanan satırlar dikkat edin. Gördüğünüz gibi temsilci gövdesi yalnızca ifadeleri, herhangi bir temsilci kümesidir. Ancak bunun yerine ayrı bir tanımı olması, biz bunu ekledik _geçici_ bizim çağrıda `FindAll()` yöntemi `List<T>` türü.

Ancak, bu yaklaşımda bile yoktur hala biz hemen atabilirsiniz kadar kod. Bu yerdir **lambda ifadeleri** oyuna gelir.

Lambda ifadeleri veya kısaca, yalnızca "Lambda'lar" C# 3.0 sürümünde, temel yapı taşlarını, dil tümleşik sorgu (LINQ) biri olarak ilk kez sunulan. Temsilcileri kullanma için yalnızca bir daha kullanışlı sözdizimi oldukları. İmza ve yöntem gövdesi bildirme, ancak bir temsilci atamazsanız, kendi resmi kimliğini yok. Temsilciler, doğrudan taraftaki olay kaydı veya çeşitli LINQ yan tümceleri ve yöntemleri olarak atanabilirler.

Lambda ifadesi bir temsilci belirtmenin yalnızca başka bir yol olduğundan, biz lambda ifadesi yerine anonim bir temsilci kullanmak için yukarıdaki örnek yeniden yapabiliyor olmanız gerekir.

```csharp
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

Vurgulanan satırlar göz atın, lambda ifadesi gibi nasıl göründüğünü görebilirsiniz. Yeniden yalnızca olan bir **çok** perde arkasında olanlar anonim temsilci ile neler için benzer şekilde, kullanma uygun söz dizimi.

Yeniden Lambda'lar, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir sorun olmadan bir olay işleyicisi olarak kullanılabilir başka bir deyişle, yalnızca temsilciler olan.

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

## <a name="further-reading-and-resources"></a>Daha fazla bilgi ve kaynaklar

*   [Temsilciler](../../docs/csharp/programming-guide/delegates/index.md)
*   [Anonim İşlevler](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [Lambda ifadeleri](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
