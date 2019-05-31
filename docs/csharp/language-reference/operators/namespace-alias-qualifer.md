---
title: ':: işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 0b456ed3ce9965ef389d8ce40167afa4ac33da18
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422530"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="16628-102">:: işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="16628-102">:: operator (C# Reference)</span></span>

<span data-ttu-id="16628-103">Ad alanı diğer ad niteleyicisi (`::`) tanımlayıcıları aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16628-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="16628-104">Her zaman, bu örnekte olduğu gibi iki tanımlayıcı arasında konumlandırılmış:</span><span class="sxs-lookup"><span data-stu-id="16628-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="16628-105">`::` İşleci de kullanılabilir olan bir *ALIAS yönergesi kullanarak*:</span><span class="sxs-lookup"><span data-stu-id="16628-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="16628-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16628-106">Remarks</span></span>

<span data-ttu-id="16628-107">Ad alanı diğer ad niteleyicisi olabilir `global`.</span><span class="sxs-lookup"><span data-stu-id="16628-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="16628-108">Bu genel ad alanı yerine bir diğer adlı ad alanı içinde bir arama başlatır.</span><span class="sxs-lookup"><span data-stu-id="16628-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="16628-109">Daha fazla bilgi için</span><span class="sxs-lookup"><span data-stu-id="16628-109">For more information</span></span>

<span data-ttu-id="16628-110">Nasıl kullanılacağına ilişkin bir örnek `::` işleci, aşağıdaki bölüme bakın:</span><span class="sxs-lookup"><span data-stu-id="16628-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="16628-111">Nasıl yapılır: Genel Namespace diğer adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="16628-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="16628-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="16628-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="16628-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16628-113">See also</span></span>

- [<span data-ttu-id="16628-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="16628-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16628-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="16628-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16628-116">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="16628-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="16628-117">. işleci</span><span class="sxs-lookup"><span data-stu-id="16628-117">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="16628-118">extern diğer adı</span><span class="sxs-lookup"><span data-stu-id="16628-118">extern alias</span></span>](../keywords/extern-alias.md)
