---
title: ':: operatör - C# referans'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 84c418627462f83630fe5072a0b0e2089f6588f6
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507132"
---
# <a name="-operator-c-reference"></a>:: operatör (C# referansı)

Diğer adı nisabı üyesine erişmek için ad alanı diğer ad niteleyicisini `::` kullanın. Niteleyiciyi `::` yalnızca iki tanımlayıcı arasında kullanabilirsiniz. Sol tanımlayıcı aşağıdaki diğer adlardan biri olabilir:

- [Bir ad yönergesi](../keywords/using-directive.md)ile oluşturulan ad alanı diğer adı:

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [Extern takma adı.](../keywords/extern-alias.md)
- Diğer `global` ad, genel ad alanı diğer adıdır. Genel ad alanı, ad alanı içinde bildirilmemiş ad alanları ve türleri içeren ad alanıdır. `::` Niteleyici ile kullanıldığında, `global` kullanıcı tanımlı `global` ad alanı diğer adı olsa bile, diğer ad her zaman genel ad alanına başvurur.

  Aşağıdaki örnek, `global` genel ad alanının <xref:System> bir üyesi olan .NET ad alanına erişmek için diğer adı kullanır. `global` Takma ad olmadan, `MyCompany.MyProduct` ad alanının bir üyesi olan kullanıcı tanımlı `System` ad alanına erişilir:

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > Anahtar `global` kelime, yalnızca `::` elemenin sol el tanımlayıcısı olduğunda genel ad alanı diğer adıdır.

Diğer adı verilen bir ad alanının bir üyesine erişmek için de belirteci kullanabilirsiniz. [ `.` ](member-access-operators.md#member-access-expression-) Ancak, `.` belirteç bir tür üyesi erişmek için de kullanılır. Niteleyici, `::` aynı ada sahip bir tür veya ad alanı olsa bile, sol el tanımlayıcısının her zaman bir ad alanı diğer adı namına başlatılmasını sağlar.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Ad Alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Ad boşluklarını kullanma](../../programming-guide/namespaces/using-namespaces.md)
