---
title: new Kısıtlaması (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269002"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="98414-102">new Kısıtlaması (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="98414-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="98414-103">`new` Kısıtlaması, hiçbir tür bağımsız değişkeni genel bir sınıf bildirimindeki genel bir parametresiz oluşturucuya sahip gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="98414-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="98414-104">New kısıtlaması kullanmak için türü soyut olamaz.</span><span class="sxs-lookup"><span data-stu-id="98414-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98414-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="98414-105">Example</span></span>  
 <span data-ttu-id="98414-106">Uygulama `new` kısıtlaması aşağıdaki örnekte gösterildiği gibi genel bir sınıf türünün yeni örneklerini oluşturduğunda, bir tür parametresi için:</span><span class="sxs-lookup"><span data-stu-id="98414-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="98414-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="98414-107">Example</span></span>  
 <span data-ttu-id="98414-108">Kullandığınızda `new()` kısıtlaması diğer kısıtlamalarla son belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="98414-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="98414-109">Daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="98414-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="98414-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="98414-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="98414-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98414-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="98414-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="98414-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="98414-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98414-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="98414-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="98414-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="98414-115">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="98414-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="98414-116">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="98414-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
