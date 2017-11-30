---
title: ":: İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b4f1683e1250ed745e15ced88203ca942c75ff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="71811-102">:: İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="71811-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="71811-103">Ad alanı diğer ad niteleyicisi (`::`) tanımlayıcıları aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71811-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="71811-104">Bu örnekte olduğu gibi iki tanımlayıcı arasında her zaman yerleştirilir:</span><span class="sxs-lookup"><span data-stu-id="71811-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="71811-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71811-105">Remarks</span></span>  
 <span data-ttu-id="71811-106">Ad alanı diğer ad niteleyicisi olabilir `global`.</span><span class="sxs-lookup"><span data-stu-id="71811-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="71811-107">Bu, bir diğer ad alanı yerine genel ad alanı bir arama başlatır.</span><span class="sxs-lookup"><span data-stu-id="71811-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="71811-108">Daha Fazla Bilgi İçin</span><span class="sxs-lookup"><span data-stu-id="71811-108">For More Information</span></span>  
 <span data-ttu-id="71811-109">Bir örnek için nasıl kullanılacağını `::` işleci, aşağıdaki bölümüne bakın:</span><span class="sxs-lookup"><span data-stu-id="71811-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="71811-110">Nasıl yapılır: Genel Namespace diğer adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="71811-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="71811-111">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="71811-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71811-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71811-112">See Also</span></span>  
 [<span data-ttu-id="71811-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="71811-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="71811-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="71811-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="71811-115">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="71811-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="71811-116">Namespace anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="71811-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="71811-117">. İşleci</span><span class="sxs-lookup"><span data-stu-id="71811-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="71811-118">extern alias</span><span class="sxs-lookup"><span data-stu-id="71811-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
