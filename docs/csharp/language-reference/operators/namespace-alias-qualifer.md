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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525662"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0283c-102">:: İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0283c-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="0283c-103">Ad alanı diğer ad niteleyicisi (`::`) tanımlayıcıları aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0283c-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="0283c-104">Her zaman, bu örnekte olduğu gibi iki tanımlayıcı arasında konumlandırılmış:</span><span class="sxs-lookup"><span data-stu-id="0283c-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="0283c-105">`::` İşleci de kullanılabilir olan bir *ALIAS yönergesi kullanarak*:</span><span class="sxs-lookup"><span data-stu-id="0283c-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="0283c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0283c-106">Remarks</span></span>  
 <span data-ttu-id="0283c-107">Ad alanı diğer ad niteleyicisi olabilir `global`.</span><span class="sxs-lookup"><span data-stu-id="0283c-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="0283c-108">Bu genel ad alanı yerine bir diğer adlı ad alanı içinde bir arama başlatır.</span><span class="sxs-lookup"><span data-stu-id="0283c-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="0283c-109">Daha Fazla Bilgi İçin</span><span class="sxs-lookup"><span data-stu-id="0283c-109">For More Information</span></span>  
 <span data-ttu-id="0283c-110">Nasıl kullanılacağına ilişkin bir örnek `::` işleci, aşağıdaki bölüme bakın:</span><span class="sxs-lookup"><span data-stu-id="0283c-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="0283c-111">Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="0283c-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="0283c-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0283c-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0283c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0283c-113">See Also</span></span>

- [<span data-ttu-id="0283c-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0283c-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0283c-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0283c-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0283c-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0283c-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="0283c-117">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0283c-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="0283c-118">. İşleç</span><span class="sxs-lookup"><span data-stu-id="0283c-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="0283c-119">extern diğer adı</span><span class="sxs-lookup"><span data-stu-id="0283c-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
