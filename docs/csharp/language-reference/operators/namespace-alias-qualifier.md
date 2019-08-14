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
# <a name="-operator-c-reference"></a><span data-ttu-id="6c3ca-102">:: işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="6c3ca-102">:: operator (C# reference)</span></span>

<span data-ttu-id="6c3ca-103">Ad alanı diğer adı niteleyicisi `::` kullanarak, diğer ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-103">Use the namespace alias qualifier `::` to access members of an aliased namespace.</span></span> <span data-ttu-id="6c3ca-104">İki tanımlayıcı arasındaki `::` niteleyiciyi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-104">You use the `::` qualifier between two identifiers.</span></span> <span data-ttu-id="6c3ca-105">Sol tanımlayıcı aşağıdaki diğer adların herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="6c3ca-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="6c3ca-106">[Using diğer adı yönergesi](../keywords/using-directive.md)ile oluşturulmuş bir ad alanı diğer adı:</span><span class="sxs-lookup"><span data-stu-id="6c3ca-106">A namespace alias created with the [using alias directive](../keywords/using-directive.md):</span></span>
  
  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="6c3ca-107">[Extern diğer adı](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="6c3ca-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="6c3ca-108">Genel ad alanı diğer adı olan diğerad.`global`</span><span class="sxs-lookup"><span data-stu-id="6c3ca-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="6c3ca-109">Genel ad alanı, adlandırılmış bir ad alanı içinde bildirilmeyen ad alanlarını ve türleri içeren ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="6c3ca-110">`::` Niteleyici ile kullanıldığında `global` , Kullanıcı tanımlı `global` ad alanı diğer adı olsa bile diğer ad her zaman genel ad alanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>
  
  <span data-ttu-id="6c3ca-111">Aşağıdaki örnek, genel ad `global` alanının bir üyesi olan .net <xref:System> ad alanına erişmek için diğer adı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="6c3ca-112">Diğer ad olmadan, `MyCompany.MyProduct` ad alanının üyesi olan `System` Kullanıcı tanımlı ad alanına erişilir: `global`</span><span class="sxs-lookup"><span data-stu-id="6c3ca-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="6c3ca-113">Anahtar sözcüğü, yalnızca `::` niteleyicinin sol tanımlayıcısı olduğunda genel ad alanı diğer adıdır. `global`</span><span class="sxs-lookup"><span data-stu-id="6c3ca-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="6c3ca-114">Diğer ad alanının üyelerine erişmek için [üye `.` erişim işlecini](member-access-operators.md#member-access-operator-) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access members of an aliased namespace.</span></span> <span data-ttu-id="6c3ca-115">`.` Ancak işleç Ayrıca bir türdeki üyelere erişmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-115">However, the `.` operator is also used to access members of a type.</span></span> <span data-ttu-id="6c3ca-116">`::` Niteleyici, aynı ada sahip bir tür veya ad alanı olsa bile sol tanımlayıcının her zaman bir ad alanı diğer adına başvurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6c3ca-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6c3ca-117">C# language specification</span></span>

<span data-ttu-id="6c3ca-118">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c3ca-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c3ca-119">See also</span></span>

- [<span data-ttu-id="6c3ca-120">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="6c3ca-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6c3ca-121">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6c3ca-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="6c3ca-122">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="6c3ca-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
