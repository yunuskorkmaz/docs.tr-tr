---
title: ':: operator- C# Reference'
ms.custom: seodec18
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
ms.openlocfilehash: 2aceb51747708b12fb3059b097b72206c78a9d5d
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971240"
---
# <a name="-operator-c-reference"></a>:: işleci (C# başvuru)

Ad alanı diğer adı niteleyicisi `::` kullanarak, diğer ad alanının üyelerine erişin. İki tanımlayıcı arasındaki `::` niteleyiciyi kullanırsınız. Sol tanımlayıcı aşağıdaki diğer adların herhangi biri olabilir:

- [Using diğer adı yönergesi](../keywords/using-directive.md)ile oluşturulmuş bir ad alanı diğer adı:
  
  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [Extern diğer adı](../keywords/extern-alias.md).
- Genel ad alanı diğer adı olan diğerad.`global` Genel ad alanı, adlandırılmış bir ad alanı içinde bildirilmeyen ad alanlarını ve türleri içeren ad alanıdır. `::` Niteleyici ile kullanıldığında `global` , Kullanıcı tanımlı `global` ad alanı diğer adı olsa bile diğer ad her zaman genel ad alanına başvurur.
  
  Aşağıdaki örnek, genel ad `global` alanının bir üyesi olan .net <xref:System> ad alanına erişmek için diğer adı kullanır. Diğer ad olmadan, `MyCompany.MyProduct` ad alanının üyesi olan `System` Kullanıcı tanımlı ad alanına erişilir: `global`

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
  > Anahtar sözcüğü, yalnızca `::` niteleyicinin sol tanımlayıcısı olduğunda genel ad alanı diğer adıdır. `global`

Diğer ad alanının üyelerine erişmek için [üye `.` erişim işlecini](member-access-operators.md#member-access-operator-) de kullanabilirsiniz. `.` Ancak işleç Ayrıca bir türdeki üyelere erişmek için de kullanılır. `::` Niteleyici, aynı ada sahip bir tür veya ad alanı olsa bile sol tanımlayıcının her zaman bir ad alanı diğer adına başvurmasını sağlar.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Ad alanlarını kullanma](../../programming-guide/namespaces/using-namespaces.md)
