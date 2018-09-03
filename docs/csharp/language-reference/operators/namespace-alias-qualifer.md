---
title: ':: İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 077d5835b372897cbe797385271effc5d00bf6e3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43473979"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a74dd-102">:: İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a74dd-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="a74dd-103">Ad alanı diğer ad niteleyicisi (`::`) tanımlayıcıları aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a74dd-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="a74dd-104">Her zaman, bu örnekte olduğu gibi iki tanımlayıcı arasında konumlandırılmış:</span><span class="sxs-lookup"><span data-stu-id="a74dd-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="a74dd-105">`::` İşleci de kullanılabilir olan bir *ALIAS yönergesi kullanarak*:</span><span class="sxs-lookup"><span data-stu-id="a74dd-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="a74dd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a74dd-106">Remarks</span></span>  
 <span data-ttu-id="a74dd-107">Ad alanı diğer ad niteleyicisi olabilir `global`.</span><span class="sxs-lookup"><span data-stu-id="a74dd-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="a74dd-108">Bu genel ad alanı yerine bir diğer adlı ad alanı içinde bir arama başlatır.</span><span class="sxs-lookup"><span data-stu-id="a74dd-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a74dd-109">Daha Fazla Bilgi İçin</span><span class="sxs-lookup"><span data-stu-id="a74dd-109">For More Information</span></span>  
 <span data-ttu-id="a74dd-110">Nasıl kullanılacağına ilişkin bir örnek `::` işleci, aşağıdaki bölüme bakın:</span><span class="sxs-lookup"><span data-stu-id="a74dd-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="a74dd-111">Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a74dd-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a74dd-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a74dd-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a74dd-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a74dd-113">See Also</span></span>

- [<span data-ttu-id="a74dd-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a74dd-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a74dd-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a74dd-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a74dd-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="a74dd-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="a74dd-117">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a74dd-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="a74dd-118">. İşleç</span><span class="sxs-lookup"><span data-stu-id="a74dd-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="a74dd-119">extern diğer adı</span><span class="sxs-lookup"><span data-stu-id="a74dd-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
