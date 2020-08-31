---
description: ':: operator-C# başvurusu'
title: ':: operator-C# başvurusu'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
- global
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 6c901ce083dde6f2e28520fafe3313071ae792c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118331"
---
# <a name="-operator-c-reference"></a>:: işleci (C# Başvurusu)

Diğer ad alanının `::` bir üyesine erişmek için ad alanı diğer adı niteleyicisi kullanın. `::`Niteleyiciyi yalnızca iki tanımlayıcı arasında kullanabilirsiniz. Sol tanımlayıcı aşağıdaki diğer adların herhangi biri olabilir:

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
- `global`Genel ad alanı diğer adı olan diğer ad. Genel ad alanı, adlandırılmış bir ad alanı içinde bildirilmeyen ad alanlarını ve türleri içeren ad alanıdır. Niteleyici ile kullanıldığında `::` , `global` Kullanıcı tanımlı `global` ad alanı diğer adı olsa bile diğer ad her zaman genel ad alanına başvurur.

  Aşağıdaki örnek, `global` <xref:System> genel ad alanının bir üyesi olan .net ad alanına erişmek için diğer adı kullanır. Diğer ad olmadan, `global` `System` ad alanının üyesi olan Kullanıcı tanımlı ad alanına `MyCompany.MyProduct` erişilir:

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
  > `global`Anahtar sözcüğü, yalnızca niteleyicinin sol tanımlayıcısı olduğunda genel ad alanı diğer adıdır `::` .

[ `.` Belirteci](member-access-operators.md#member-access-expression-) Ayrıca, diğer ad alanının bir üyesine erişmek için de kullanabilirsiniz. Ancak, `.` belirteç bir tür üyesine erişmek için de kullanılır. `::`Niteleyici, aynı ada sahip bir tür veya ad alanı olsa bile sol tanımlayıcının her zaman bir ad alanı diğer adına başvurmasını sağlar.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Ad alanlarını kullanma](../../programming-guide/namespaces/using-namespaces.md)
