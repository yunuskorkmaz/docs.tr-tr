---
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
ms.openlocfilehash: f91287ed281a2c6b10bed93cff10b08972a8445e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855133"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7dd52-102">:: işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7dd52-102">:: operator (C# reference)</span></span>

<span data-ttu-id="7dd52-103">Diğer ad alanının `::` bir üyesine erişmek için ad alanı diğer adı niteleyicisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7dd52-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="7dd52-104">`::`Niteleyiciyi yalnızca iki tanımlayıcı arasında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dd52-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="7dd52-105">Sol tanımlayıcı aşağıdaki diğer adların herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="7dd52-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="7dd52-106">Bir [using diğer adı yönergesi](../keywords/using-directive.md)ile oluşturulmuş bir ad alanı diğer adı:</span><span class="sxs-lookup"><span data-stu-id="7dd52-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="7dd52-107">[Extern diğer adı](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="7dd52-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="7dd52-108">`global`Genel ad alanı diğer adı olan diğer ad.</span><span class="sxs-lookup"><span data-stu-id="7dd52-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="7dd52-109">Genel ad alanı, adlandırılmış bir ad alanı içinde bildirilmeyen ad alanlarını ve türleri içeren ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="7dd52-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="7dd52-110">Niteleyici ile kullanıldığında `::` , `global` Kullanıcı tanımlı `global` ad alanı diğer adı olsa bile diğer ad her zaman genel ad alanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="7dd52-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="7dd52-111">Aşağıdaki örnek, `global` <xref:System> genel ad alanının bir üyesi olan .net ad alanına erişmek için diğer adı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7dd52-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="7dd52-112">Diğer ad olmadan, `global` `System` ad alanının üyesi olan Kullanıcı tanımlı ad alanına `MyCompany.MyProduct` erişilir:</span><span class="sxs-lookup"><span data-stu-id="7dd52-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="7dd52-113">`global`Anahtar sözcüğü, yalnızca niteleyicinin sol tanımlayıcısı olduğunda genel ad alanı diğer adıdır `::` .</span><span class="sxs-lookup"><span data-stu-id="7dd52-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="7dd52-114">[ `.` Belirteci](member-access-operators.md#member-access-expression-) Ayrıca, diğer ad alanının bir üyesine erişmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dd52-114">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="7dd52-115">Ancak, `.` belirteç bir tür üyesine erişmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7dd52-115">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="7dd52-116">`::`Niteleyici, aynı ada sahip bir tür veya ad alanı olsa bile sol tanımlayıcının her zaman bir ad alanı diğer adına başvurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dd52-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7dd52-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7dd52-117">C# language specification</span></span>

<span data-ttu-id="7dd52-118">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanı diğer ad niteleyicileri](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7dd52-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7dd52-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd52-119">See also</span></span>

- [<span data-ttu-id="7dd52-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7dd52-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7dd52-121">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="7dd52-121">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="7dd52-122">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="7dd52-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
