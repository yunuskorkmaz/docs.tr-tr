---
title: "private (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords: private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a><span data-ttu-id="0c201-102">private (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0c201-102">private (C# Reference)</span></span>
<span data-ttu-id="0c201-103">`private` Sözcüktür üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0c201-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="0c201-104">Bu sayfayı kapsayan `private` erişim.</span><span class="sxs-lookup"><span data-stu-id="0c201-104">This page covers `private` access.</span></span> <span data-ttu-id="0c201-105">`private` Sözcüktür ayrıca parçası [ `private protected` ](./private-protected.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0c201-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="0c201-106">Özel erişim en az izin veren bir erişim düzeydir.</span><span class="sxs-lookup"><span data-stu-id="0c201-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="0c201-107">Özel üyeler, yalnızca sınıf ya da, bunlar, bu örnekteki bildirilir yapı gövdesi içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="0c201-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="0c201-108">İç içe geçmiş türler aynı gövdesinde, bu özel üyeler de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c201-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="0c201-109">Özel üye sınıfta veya yapı içinde bildirilmiş dışında başvurmak için bir derleme zamanı hata var.</span><span class="sxs-lookup"><span data-stu-id="0c201-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="0c201-110">Bir karşılaştırması `private` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="0c201-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c201-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c201-111">Example</span></span>  
 <span data-ttu-id="0c201-112">Bu örnekte, `Employee` sınıfı içeren iki özel veri üyesi `name` ve `salary`.</span><span class="sxs-lookup"><span data-stu-id="0c201-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="0c201-113">Özel üye olarak, bunlar dışındaki üye yöntemleri tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="0c201-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="0c201-114">Genel yöntemler adlı `GetName` ve `Salary` özel üyelerin denetimli erişmesine izin vermek için eklenir.</span><span class="sxs-lookup"><span data-stu-id="0c201-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="0c201-115">`name` Üye genel bir yöntem aracılığıyla erişilen ve `salary` üye genel salt okunur özelliği aracılığıyla erişilir.</span><span class="sxs-lookup"><span data-stu-id="0c201-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="0c201-116">(Bkz [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) daha fazla bilgi için.)</span><span class="sxs-lookup"><span data-stu-id="0c201-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0c201-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0c201-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0c201-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c201-118">See Also</span></span>  
 [<span data-ttu-id="0c201-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0c201-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0c201-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0c201-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0c201-121">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0c201-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0c201-122">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="0c201-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="0c201-123">Erişilebilirlik düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0c201-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="0c201-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="0c201-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="0c201-125">Ortak</span><span class="sxs-lookup"><span data-stu-id="0c201-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="0c201-126">korumalı</span><span class="sxs-lookup"><span data-stu-id="0c201-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="0c201-127">İç</span><span class="sxs-lookup"><span data-stu-id="0c201-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
