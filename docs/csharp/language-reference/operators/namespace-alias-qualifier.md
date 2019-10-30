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
# <a name="-operator-c-reference"></a><span data-ttu-id="35139-102">:: işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="35139-102">:: operator (C# reference)</span></span>

<span data-ttu-id="35139-103">Ad alanı diğer adı niteleyicisi `::`, diğer ad alanının bir üyesine erişmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="35139-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="35139-104">`::` niteleyicisi yalnızca iki tanımlayıcı arasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35139-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="35139-105">Sol tanımlayıcı aşağıdaki diğer adların herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="35139-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="35139-106">Bir [using diğer adı yönergesi](../keywords/using-directive.md)ile oluşturulmuş bir ad alanı diğer adı:</span><span class="sxs-lookup"><span data-stu-id="35139-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="35139-107">[Extern diğer adı](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="35139-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="35139-108">Genel ad alanı diğer adı olan `global` diğer adı.</span><span class="sxs-lookup"><span data-stu-id="35139-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="35139-109">Genel ad alanı, adlandırılmış bir ad alanı içinde bildirilmeyen ad alanlarını ve türleri içeren ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="35139-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="35139-110">`::` niteleyicisi ile kullanıldığında, Kullanıcı tanımlı `global` ad alanı diğer adı olsa da, `global` diğer adı her zaman genel ad alanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="35139-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="35139-111">Aşağıdaki örnek, genel ad alanının bir üyesi olan .NET <xref:System> ad alanına erişmek için `global` diğer adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="35139-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="35139-112">`global` diğer adı olmadan, `MyCompany.MyProduct` ad alanının üyesi olan Kullanıcı tanımlı `System` ad alanına erişilir:</span><span class="sxs-lookup"><span data-stu-id="35139-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="35139-113">`global` anahtar sözcüğü, yalnızca `::` niteleyicisi sol tarafınında olan genel ad alanı diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="35139-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="35139-114">Ayrıca, diğer ad alanının bir üyesine erişmek için [üye erişimi `.` işlecini](member-access-operators.md#member-access-operator-) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35139-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="35139-115">Ancak, `.` işleci bir tür üyesine erişmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35139-115">However, the `.` operator is also used to access a type member.</span></span> <span data-ttu-id="35139-116">`::` niteleyicisi, aynı ada sahip bir tür veya ad alanı olsa da, sol taraftaki tanımlayıcının her zaman bir ad alanı diğer adına başvurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="35139-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="35139-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="35139-117">C# language specification</span></span>

<span data-ttu-id="35139-118">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="35139-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="35139-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35139-119">See also</span></span>

- [<span data-ttu-id="35139-120">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="35139-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="35139-121">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="35139-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="35139-122">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="35139-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
