---
title: Erişilebilirlik düzeylerini kullanma kısıtlamaları - C# Reference
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173542"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="b04cb-102">Erişilebilirlik düzeylerinin kullanımına ilişkin kısıtlamalar (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="b04cb-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="b04cb-103">Bir bildirimde bir tür belirttiğiniz zaman, türün erişilebilirlik düzeyinin bir üyenin veya başka bir türün erişilebilirlik düzeyine bağlı olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b04cb-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="b04cb-104">Örneğin, doğrudan taban sınıf en az türemiş sınıf kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="b04cb-105">Taban sınıf `BaseClass` aşağıdakilerden daha az erişilebilir olduğundan derleyici `MyClass`hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="b04cb-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="b04cb-106">Aşağıdaki tablo, bildirilen erişilebilirlik düzeylerine ilişkin kısıtlamaları özetleyin.</span><span class="sxs-lookup"><span data-stu-id="b04cb-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="b04cb-107">Bağlam</span><span class="sxs-lookup"><span data-stu-id="b04cb-107">Context</span></span>|<span data-ttu-id="b04cb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b04cb-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="b04cb-109">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b04cb-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="b04cb-110">Bir sınıf türünün doğrudan taban sınıfı en az sınıf türü kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="b04cb-111">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b04cb-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="b04cb-112">Arabirim türünün açık temel arabirimleri en az arabirim türü kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="b04cb-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="b04cb-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="b04cb-114">Temsilci türünün dönüş türü ve parametre türleri en az temsilci türü kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="b04cb-115">Sabitler</span><span class="sxs-lookup"><span data-stu-id="b04cb-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="b04cb-116">Sabitin türü en az sabitin kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="b04cb-117">Alanlar</span><span class="sxs-lookup"><span data-stu-id="b04cb-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="b04cb-118">Bir alanın türü en az alanın kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="b04cb-119">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b04cb-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="b04cb-120">Bir yöntemin dönüş türü ve parametre türleri en az yöntemin kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="b04cb-121">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b04cb-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="b04cb-122">Bir özelliğin türü en az özelliğin kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="b04cb-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b04cb-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="b04cb-124">Bir olayın türü en az olayın kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="b04cb-125">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b04cb-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="b04cb-126">Dizinleyicinin türü ve parametre türleri en az dizinleyicinin kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="b04cb-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="b04cb-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="b04cb-128">Bir işleçin dönüş türü ve parametre türleri en az operatörün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="b04cb-129">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b04cb-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="b04cb-130">Bir oluşturucuparametre türleri en az yapıcının kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04cb-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="b04cb-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="b04cb-131">Example</span></span>

<span data-ttu-id="b04cb-132">Aşağıdaki örnek, farklı türde hatalı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b04cb-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="b04cb-133">Her bildirimi izleyen açıklama beklenen derleyici hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b04cb-133">The comment following each declaration indicates the expected compiler error.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="b04cb-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b04cb-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b04cb-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b04cb-135">See also</span></span>

- [<span data-ttu-id="b04cb-136">C# Referans</span><span class="sxs-lookup"><span data-stu-id="b04cb-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="b04cb-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b04cb-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b04cb-138">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="b04cb-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="b04cb-139">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b04cb-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="b04cb-140">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="b04cb-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="b04cb-141">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b04cb-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="b04cb-142">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b04cb-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="b04cb-143">Kamu</span><span class="sxs-lookup"><span data-stu-id="b04cb-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="b04cb-144">Özel</span><span class="sxs-lookup"><span data-stu-id="b04cb-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="b04cb-145">protected</span><span class="sxs-lookup"><span data-stu-id="b04cb-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="b04cb-146">Iç</span><span class="sxs-lookup"><span data-stu-id="b04cb-146">internal</span></span>](../../language-reference/keywords/internal.md)
