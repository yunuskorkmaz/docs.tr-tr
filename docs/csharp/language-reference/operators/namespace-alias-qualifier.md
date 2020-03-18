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
ms.openlocfilehash: a18e52ea05d49bf2b3a468923f1433f09fff9a8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712682"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="582a5-102">:: operatör (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="582a5-102">:: operator (C# reference)</span></span>

<span data-ttu-id="582a5-103">Diğer adı nisabı üyesine erişmek için ad alanı diğer ad niteleyicisini `::` kullanın.</span><span class="sxs-lookup"><span data-stu-id="582a5-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="582a5-104">Niteleyiciyi `::` yalnızca iki tanımlayıcı arasında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="582a5-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="582a5-105">Sol tanımlayıcı aşağıdaki diğer adlardan biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="582a5-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="582a5-106">[Bir ad yönergesi](../keywords/using-directive.md)ile oluşturulan ad alanı diğer adı:</span><span class="sxs-lookup"><span data-stu-id="582a5-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="582a5-107">[Extern takma adı.](../keywords/extern-alias.md)</span><span class="sxs-lookup"><span data-stu-id="582a5-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="582a5-108">Diğer `global` ad, genel ad alanı diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="582a5-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="582a5-109">Genel ad alanı, ad alanı içinde bildirilmemiş ad alanları ve türleri içeren ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="582a5-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="582a5-110">`::` Niteleyici ile kullanıldığında, `global` kullanıcı tanımlı `global` ad alanı diğer adı olsa bile, diğer ad her zaman genel ad alanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="582a5-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="582a5-111">Aşağıdaki örnek, `global` genel ad alanının <xref:System> bir üyesi olan .NET ad alanına erişmek için diğer adı kullanır.</span><span class="sxs-lookup"><span data-stu-id="582a5-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="582a5-112">`global` Takma ad olmadan, `MyCompany.MyProduct` ad alanının bir üyesi olan kullanıcı tanımlı `System` ad alanına erişilir:</span><span class="sxs-lookup"><span data-stu-id="582a5-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="582a5-113">Anahtar `global` kelime, yalnızca `::` elemenin sol el tanımlayıcısı olduğunda genel ad alanı diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="582a5-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="582a5-114">Diğer adı alan bir üyeye erişmek için [üye erişim `.` işlecini](member-access-operators.md#member-access-operator-) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="582a5-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="582a5-115">Ancak, `.` işleç bir tür üyesi erişmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="582a5-115">However, the `.` operator is also used to access a type member.</span></span> <span data-ttu-id="582a5-116">Niteleyici, `::` aynı ada sahip bir tür veya ad alanı olsa bile, sol el tanımlayıcısının her zaman bir ad alanı diğer adı namına başlatılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="582a5-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="582a5-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="582a5-117">C# language specification</span></span>

<span data-ttu-id="582a5-118">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Ad Alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="582a5-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="582a5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="582a5-119">See also</span></span>

- [<span data-ttu-id="582a5-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="582a5-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="582a5-121">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="582a5-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="582a5-122">Ad boşluklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="582a5-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
