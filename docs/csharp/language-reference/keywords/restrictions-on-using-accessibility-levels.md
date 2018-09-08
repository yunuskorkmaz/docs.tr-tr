---
title: (C# Başvurusu) erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 2bcf2b12d1aa1488e6d3e46f5b37ac9535b138dd
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140521"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="2e6e0-102">(C# Başvurusu) erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="2e6e0-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="2e6e0-103">Bir bildirim türü belirttiğinizde, türün erişilebilirlik düzeyi erişilebilirlik düzeyine üyesi veya başka bir türe bağımlı olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="2e6e0-104">Örneğin, doğrudan temel sınıf en az türetilen sınıf olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="2e6e0-105">Aşağıdaki bildirimleri için bir derleyici hatasına neden temel sınıf `BaseClass` daha az erişilebilir `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="2e6e0-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="2e6e0-106">Bildirilen erişilebilirlik düzeyi kısıtlamaları aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="2e6e0-107">Bağlam</span><span class="sxs-lookup"><span data-stu-id="2e6e0-107">Context</span></span>|<span data-ttu-id="2e6e0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e6e0-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="2e6e0-109">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="2e6e0-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="2e6e0-110">Bir sınıf türünün doğrudan temel sınıf en az sınıf türü kendisini olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="2e6e0-111">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="2e6e0-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="2e6e0-112">Açık bir arabirim türü temel arabirimleri en az arabirim türü kendisini olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="2e6e0-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="2e6e0-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="2e6e0-114">Bir temsilci türü parametre türleri ve dönüş türü, en az temsilci türü kendisini olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="2e6e0-115">Sabitler</span><span class="sxs-lookup"><span data-stu-id="2e6e0-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="2e6e0-116">Bir sabit değer türü en az sabit olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="2e6e0-117">Alanlar</span><span class="sxs-lookup"><span data-stu-id="2e6e0-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="2e6e0-118">Bir alan türü en az alan olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="2e6e0-119">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2e6e0-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="2e6e0-120">Bir yöntemin parametre türleri ve dönüş türü, en az yöntemi olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="2e6e0-121">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2e6e0-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="2e6e0-122">Bir özelliğin türünü en az özelliği olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="2e6e0-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="2e6e0-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="2e6e0-124">Bir olay türü en az olay olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="2e6e0-125">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2e6e0-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="2e6e0-126">Bir dizin oluşturucu türü ve parametre türleri, en az Indexer olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="2e6e0-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="2e6e0-127">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="2e6e0-128">Operatör için parametre türleri ve dönüş türü, en azından operatör olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="2e6e0-129">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2e6e0-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="2e6e0-130">Parametre türleri bir oluşturucunun en az Oluşturucu olarak olarak erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="2e6e0-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e6e0-131">Example</span></span>

<span data-ttu-id="2e6e0-132">Aşağıdaki örnek, farklı türlerdeki hatalı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="2e6e0-133">Her bildiriminin açıklama beklenen derleyici hata olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-133">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
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

## <a name="c-language-specification"></a><span data-ttu-id="2e6e0-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2e6e0-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2e6e0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e6e0-135">See also</span></span>

- [<span data-ttu-id="2e6e0-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2e6e0-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="2e6e0-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2e6e0-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2e6e0-138">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2e6e0-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="2e6e0-139">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="2e6e0-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="2e6e0-140">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="2e6e0-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="2e6e0-141">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="2e6e0-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="2e6e0-142">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="2e6e0-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="2e6e0-143">public</span><span class="sxs-lookup"><span data-stu-id="2e6e0-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="2e6e0-144">private</span><span class="sxs-lookup"><span data-stu-id="2e6e0-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="2e6e0-145">protected</span><span class="sxs-lookup"><span data-stu-id="2e6e0-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="2e6e0-146">internal</span><span class="sxs-lookup"><span data-stu-id="2e6e0-146">internal</span></span>](../../language-reference/keywords/internal.md)