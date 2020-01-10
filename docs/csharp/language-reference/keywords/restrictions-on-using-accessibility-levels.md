---
title: Erişilebilirlik düzeylerini kullanma kısıtlamaları- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 90c76e68ca526106f3a8be6e3db2640edbb2bc80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715157"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="6c190-102">Erişilebilirlik düzeylerini kullanma kısıtlamaları (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="6c190-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="6c190-103">Bir bildirimde bir tür belirttiğinizde, türün erişilebilirlik düzeyinin bir üyenin ya da başka bir türün erişilebilirlik düzeyine bağımlı olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="6c190-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="6c190-104">Örneğin, doğrudan temel sınıfı en azından türetilmiş sınıf olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="6c190-105">Temel sınıf `BaseClass` `MyClass`daha az erişilebilir olduğu için aşağıdaki bildirimler bir derleyici hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="6c190-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="6c190-106">Aşağıdaki tablo, belirtilen erişilebilirlik düzeyleri üzerindeki kısıtlamaları özetler.</span><span class="sxs-lookup"><span data-stu-id="6c190-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="6c190-107">Bağlam</span><span class="sxs-lookup"><span data-stu-id="6c190-107">Context</span></span>|<span data-ttu-id="6c190-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c190-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="6c190-109">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="6c190-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="6c190-110">Bir sınıf türünün doğrudan temel sınıfı en azından sınıf türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="6c190-111">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6c190-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="6c190-112">Arabirim türünün açık temel arabirimleri en az arabirim türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="6c190-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="6c190-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="6c190-114">Bir temsilci türünün dönüş türü ve parametre türleri en azından temsilci türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="6c190-115">Sabitler</span><span class="sxs-lookup"><span data-stu-id="6c190-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="6c190-116">Bir sabit türü en az sabit değer olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="6c190-117">Alanlar</span><span class="sxs-lookup"><span data-stu-id="6c190-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="6c190-118">Alanın türü en azından alanın kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="6c190-119">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6c190-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="6c190-120">Bir yöntemin dönüş türü ve parametre türleri en az yöntemin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="6c190-121">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="6c190-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="6c190-122">Özelliğin türü en az özelliğin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="6c190-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="6c190-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="6c190-124">Bir olayın türü en az olayın kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="6c190-125">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="6c190-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="6c190-126">Bir dizin oluşturucunun türü ve parametre türleri en azından dizin oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="6c190-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="6c190-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="6c190-128">Bir işlecin dönüş türü ve parametre türleri en az işlecin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="6c190-129">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="6c190-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="6c190-130">Bir oluşturucunun parametre türleri en az oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c190-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="6c190-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c190-131">Example</span></span>

<span data-ttu-id="6c190-132">Aşağıdaki örnek farklı türlerin hatalı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6c190-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="6c190-133">Her bildirimi izleyen yorum, beklenen derleyici hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c190-133">The comment following each declaration indicates the expected compiler error.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="6c190-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6c190-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6c190-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c190-135">See also</span></span>

- [<span data-ttu-id="6c190-136">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="6c190-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="6c190-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6c190-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6c190-138">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6c190-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="6c190-139">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="6c190-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="6c190-140">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="6c190-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="6c190-141">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="6c190-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="6c190-142">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="6c190-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="6c190-143">public</span><span class="sxs-lookup"><span data-stu-id="6c190-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="6c190-144">private</span><span class="sxs-lookup"><span data-stu-id="6c190-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="6c190-145">protected</span><span class="sxs-lookup"><span data-stu-id="6c190-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="6c190-146">internal</span><span class="sxs-lookup"><span data-stu-id="6c190-146">internal</span></span>](../../language-reference/keywords/internal.md)
