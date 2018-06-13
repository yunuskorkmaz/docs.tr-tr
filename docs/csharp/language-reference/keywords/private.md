---
title: private (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 89bc23e91bf693f0a95b75dffe2399cb7e865b50
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171869"
---
# <a name="private-c-reference"></a><span data-ttu-id="5df4d-102">private (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5df4d-102">private (C# Reference)</span></span>
<span data-ttu-id="5df4d-103">`private` Sözcüktür üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5df4d-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="5df4d-104">Bu sayfayı kapsayan `private` erişim.</span><span class="sxs-lookup"><span data-stu-id="5df4d-104">This page covers `private` access.</span></span> <span data-ttu-id="5df4d-105">`private` Sözcüktür ayrıca parçası [ `private protected` ](./private-protected.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5df4d-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="5df4d-106">Özel erişim en az izin veren bir erişim düzeydir.</span><span class="sxs-lookup"><span data-stu-id="5df4d-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="5df4d-107">Özel üyeler, yalnızca sınıf ya da, bunlar, bu örnekteki bildirilir yapı gövdesi içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="5df4d-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```csharp  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="5df4d-108">İç içe geçmiş türler aynı gövdesinde, bu özel üyeler de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5df4d-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="5df4d-109">Özel üye sınıfta veya yapı içinde bildirilmiş dışında başvurmak için bir derleme zamanı hata var.</span><span class="sxs-lookup"><span data-stu-id="5df4d-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="5df4d-110">Bir karşılaştırması `private` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="5df4d-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5df4d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5df4d-111">Example</span></span>  
 <span data-ttu-id="5df4d-112">Bu örnekte, `Employee` sınıfı içeren iki özel veri üyesi `name` ve `salary`.</span><span class="sxs-lookup"><span data-stu-id="5df4d-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="5df4d-113">Özel üye olarak, bunlar dışındaki üye yöntemleri tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="5df4d-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="5df4d-114">Genel yöntemler adlı `GetName` ve `Salary` özel üyelerin denetimli erişmesine izin vermek için eklenir.</span><span class="sxs-lookup"><span data-stu-id="5df4d-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="5df4d-115">`name` Üye genel bir yöntem aracılığıyla erişilen ve `salary` üye genel salt okunur özelliği aracılığıyla erişilir.</span><span class="sxs-lookup"><span data-stu-id="5df4d-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="5df4d-116">(Bkz [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) daha fazla bilgi için.)</span><span class="sxs-lookup"><span data-stu-id="5df4d-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5df4d-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5df4d-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5df4d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5df4d-118">See Also</span></span>  
 [<span data-ttu-id="5df4d-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5df4d-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5df4d-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5df4d-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5df4d-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5df4d-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5df4d-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="5df4d-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="5df4d-123">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="5df4d-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="5df4d-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5df4d-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="5df4d-125">public</span><span class="sxs-lookup"><span data-stu-id="5df4d-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="5df4d-126">protected</span><span class="sxs-lookup"><span data-stu-id="5df4d-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="5df4d-127">internal</span><span class="sxs-lookup"><span data-stu-id="5df4d-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
