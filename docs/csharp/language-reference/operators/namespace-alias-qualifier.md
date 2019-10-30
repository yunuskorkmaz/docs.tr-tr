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
ms.openlocfilehash: 97ed24b050f79cf44ffd1c03c213ffcf91758260
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038986"
---
# <a name="-operator-c-reference"></a>:: işleci (C# başvuru)

Ad alanı diğer adı niteleyicisi `::`, diğer ad alanının bir üyesine erişmek için kullanın. `::` niteleyicisi yalnızca iki tanımlayıcı arasında kullanılabilir. Sol tanımlayıcı aşağıdaki diğer adların herhangi biri olabilir:

- Bir [using diğer adı yönergesi](../keywords/using-directive.md)ile oluşturulmuş bir ad alanı diğer adı:

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [Extern diğer adı](../keywords/extern-alias.md).
- Genel ad alanı diğer adı olan `global` diğer adı. Genel ad alanı, adlandırılmış bir ad alanı içinde bildirilmeyen ad alanlarını ve türleri içeren ad alanıdır. `::` niteleyicisi ile kullanıldığında, Kullanıcı tanımlı `global` ad alanı diğer adı olsa da, `global` diğer adı her zaman genel ad alanına başvurur.

  Aşağıdaki örnek, genel ad alanının bir üyesi olan .NET <xref:System> ad alanına erişmek için `global` diğer adını kullanır. `global` diğer adı olmadan, `MyCompany.MyProduct` ad alanının üyesi olan Kullanıcı tanımlı `System` ad alanına erişilir:

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
  > `global` anahtar sözcüğü, yalnızca `::` niteleyicisi sol tarafınında olan genel ad alanı diğer adıdır.

Ayrıca, diğer ad alanının bir üyesine erişmek için [üye erişimi `.` işlecini](member-access-operators.md#member-access-operator-) de kullanabilirsiniz. Ancak, `.` işleci bir tür üyesine erişmek için de kullanılır. `::` niteleyicisi, aynı ada sahip bir tür veya ad alanı olsa da, sol taraftaki tanımlayıcının her zaman bir ad alanı diğer adına başvurmasını sağlar.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Ad alanlarını kullanma](../../programming-guide/namespaces/using-namespaces.md)
