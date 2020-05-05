---
title: Erişilebilirlik düzeylerini kullanma kısıtlamaları-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 8082dbd7398b6634b68f1dd2887cd55d6798a5d9
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795163"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="05a6c-102">Erişilebilirlik düzeylerini kullanma kısıtlamaları (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="05a6c-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="05a6c-103">Bir bildirimde bir tür belirttiğinizde, türün erişilebilirlik düzeyinin bir üyenin ya da başka bir türün erişilebilirlik düzeyine bağımlı olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="05a6c-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="05a6c-104">Örneğin, doğrudan temel sınıfı en azından türetilmiş sınıf olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="05a6c-105">Aşağıdaki bildirimler bir derleyici hatasına neden olur çünkü temel sınıf `BaseClass` şundan `MyClass`daha az erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="05a6c-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="05a6c-106">Aşağıdaki tablo, belirtilen erişilebilirlik düzeyleri üzerindeki kısıtlamaları özetler.</span><span class="sxs-lookup"><span data-stu-id="05a6c-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="05a6c-107">Bağlam</span><span class="sxs-lookup"><span data-stu-id="05a6c-107">Context</span></span>|<span data-ttu-id="05a6c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05a6c-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="05a6c-109">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="05a6c-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="05a6c-110">Bir sınıf türünün doğrudan temel sınıfı en azından sınıf türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="05a6c-111">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="05a6c-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="05a6c-112">Arabirim türünün açık temel arabirimleri en az arabirim türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="05a6c-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="05a6c-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="05a6c-114">Bir temsilci türünün dönüş türü ve parametre türleri en azından temsilci türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="05a6c-115">Sabitler</span><span class="sxs-lookup"><span data-stu-id="05a6c-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="05a6c-116">Bir sabit türü en az sabit değer olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="05a6c-117">Alanlar</span><span class="sxs-lookup"><span data-stu-id="05a6c-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="05a6c-118">Alanın türü en azından alanın kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="05a6c-119">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="05a6c-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="05a6c-120">Bir yöntemin dönüş türü ve parametre türleri en az yöntemin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="05a6c-121">Özellikler</span><span class="sxs-lookup"><span data-stu-id="05a6c-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="05a6c-122">Özelliğin türü en az özelliğin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="05a6c-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="05a6c-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="05a6c-124">Bir olayın türü en az olayın kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="05a6c-125">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="05a6c-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="05a6c-126">Bir dizin oluşturucunun türü ve parametre türleri en azından dizin oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="05a6c-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="05a6c-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="05a6c-128">Bir işlecin dönüş türü ve parametre türleri en az işlecin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="05a6c-129">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="05a6c-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="05a6c-130">Bir oluşturucunun parametre türleri en az oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05a6c-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="05a6c-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="05a6c-131">Example</span></span>

<span data-ttu-id="05a6c-132">Aşağıdaki örnek farklı türlerin hatalı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="05a6c-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="05a6c-133">Her bildirimi izleyen yorum, beklenen derleyici hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="05a6c-133">The comment following each declaration indicates the expected compiler error.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="05a6c-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="05a6c-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="05a6c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05a6c-135">See also</span></span>

- [<span data-ttu-id="05a6c-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="05a6c-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05a6c-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="05a6c-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05a6c-138">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="05a6c-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="05a6c-139">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="05a6c-139">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="05a6c-140">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="05a6c-140">Accessibility Domain</span></span>](accessibility-domain.md)
- [<span data-ttu-id="05a6c-141">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="05a6c-141">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="05a6c-142">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="05a6c-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="05a6c-143">public</span><span class="sxs-lookup"><span data-stu-id="05a6c-143">public</span></span>](public.md)
- [<span data-ttu-id="05a6c-144">private</span><span class="sxs-lookup"><span data-stu-id="05a6c-144">private</span></span>](private.md)
- [<span data-ttu-id="05a6c-145">protected</span><span class="sxs-lookup"><span data-stu-id="05a6c-145">protected</span></span>](protected.md)
- [<span data-ttu-id="05a6c-146">internal</span><span class="sxs-lookup"><span data-stu-id="05a6c-146">internal</span></span>](internal.md)
