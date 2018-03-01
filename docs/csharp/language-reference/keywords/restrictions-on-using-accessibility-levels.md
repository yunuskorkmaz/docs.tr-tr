---
title: "Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44d065429f67d717d7c50e3877294eadd462a99d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="eb738-102">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eb738-102">Restrictions on Using Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="eb738-103">Bir bildiriminde bir türü belirttiğinizde, türü erişilebilirlik düzeyi erişilebilirlik düzeyinde bir üye veya başka bir türde bağımlı olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="eb738-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="eb738-104">Örneğin, doğrudan temel sınıf en az türetilmiş sınıf olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="eb738-105">Aşağıdaki bildirimler için derleyici hatası neden temel sınıfı `BaseClass` daha az erişilebilen `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="eb738-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 <span data-ttu-id="eb738-106">Aşağıdaki tabloda bildirilen erişilebilirlik düzeyi kısıtlamaları özetlenir.</span><span class="sxs-lookup"><span data-stu-id="eb738-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>  
  
|<span data-ttu-id="eb738-107">Bağlam</span><span class="sxs-lookup"><span data-stu-id="eb738-107">Context</span></span>|<span data-ttu-id="eb738-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb738-108">Remarks</span></span>|  
|-------------|-------------|  
|[<span data-ttu-id="eb738-109">Sınıfları</span><span class="sxs-lookup"><span data-stu-id="eb738-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="eb738-110">Sınıf türü doğrudan temel sınıfını en az sınıf türü kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|  
|[<span data-ttu-id="eb738-111">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb738-111">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)|<span data-ttu-id="eb738-112">Bir arabirim türünün açık temel arabirimler en az arabirim türü kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|  
|[<span data-ttu-id="eb738-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="eb738-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)|<span data-ttu-id="eb738-114">Dönüş türü ve bir temsilci türü parametre türleri, en az temsilci türü olarak kendisi olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb738-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|  
|[<span data-ttu-id="eb738-115">Sabitleri</span><span class="sxs-lookup"><span data-stu-id="eb738-115">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="eb738-116">Bir sabit türü en az sabit olarak olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|  
|[<span data-ttu-id="eb738-117">Alanları</span><span class="sxs-lookup"><span data-stu-id="eb738-117">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="eb738-118">Bir alan türü en az alan olarak olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-118">The type of a field must be at least as accessible as the field itself.</span></span>|  
|[<span data-ttu-id="eb738-119">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="eb738-119">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="eb738-120">Bir yöntemin parametre türleri ve dönüş türü, en az yöntemi olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb738-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|  
|[<span data-ttu-id="eb738-121">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="eb738-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="eb738-122">Bir özelliğin türünü en az özelliği olarak olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-122">The type of a property must be at least as accessible as the property itself.</span></span>|  
|[<span data-ttu-id="eb738-123">Olayları</span><span class="sxs-lookup"><span data-stu-id="eb738-123">Events</span></span>](../../../csharp/programming-guide/events/index.md)|<span data-ttu-id="eb738-124">Bir olay türü en az olayı olarak olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-124">The type of an event must be at least as accessible as the event itself.</span></span>|  
|[<span data-ttu-id="eb738-125">Dizin oluşturucular</span><span class="sxs-lookup"><span data-stu-id="eb738-125">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)|<span data-ttu-id="eb738-126">Bir dizin oluşturucu türü ve parametre türleri en az dizinleyici olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|  
|[<span data-ttu-id="eb738-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="eb738-127">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="eb738-128">Dönüş türü ve bir işleç parametre türleri, en azından operatör olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb738-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|  
|[<span data-ttu-id="eb738-129">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="eb738-129">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="eb738-130">Bir oluşturucu parametre türleri en az oluşturucusu olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb738-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eb738-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb738-131">Example</span></span>  
 <span data-ttu-id="eb738-132">Aşağıdaki örnek, farklı türlerde hatalı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="eb738-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="eb738-133">Her bildirim aşağıdaki açıklama beklenen derleyici hatası gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb738-133">The comment following each declaration indicates the expected compiler error.</span></span>  
  
```  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
    }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="eb738-134">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="eb738-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb738-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb738-135">See Also</span></span>  
 [<span data-ttu-id="eb738-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="eb738-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="eb738-137">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb738-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eb738-138">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="eb738-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="eb738-139">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="eb738-139">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="eb738-140">Erişilebilirlik etki alanı</span><span class="sxs-lookup"><span data-stu-id="eb738-140">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="eb738-141">Erişilebilirlik düzeyleri</span><span class="sxs-lookup"><span data-stu-id="eb738-141">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="eb738-142">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="eb738-142">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="eb738-143">Ortak</span><span class="sxs-lookup"><span data-stu-id="eb738-143">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="eb738-144">Özel</span><span class="sxs-lookup"><span data-stu-id="eb738-144">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="eb738-145">korumalı</span><span class="sxs-lookup"><span data-stu-id="eb738-145">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="eb738-146">İç</span><span class="sxs-lookup"><span data-stu-id="eb738-146">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
