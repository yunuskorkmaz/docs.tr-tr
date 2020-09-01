---
description: Erişilebilirlik düzeylerini kullanma kısıtlamaları-C# başvurusu
title: Erişilebilirlik düzeylerini kullanma kısıtlamaları-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 542e463e41c70f2e8aed5c20dc1294e296a88518
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137011"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="1d134-103">Erişilebilirlik düzeylerini kullanma kısıtlamaları (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1d134-103">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="1d134-104">Bir bildirimde bir tür belirttiğinizde, türün erişilebilirlik düzeyinin bir üyenin ya da başka bir türün erişilebilirlik düzeyine bağımlı olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="1d134-104">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="1d134-105">Örneğin, doğrudan temel sınıfı en azından türetilmiş sınıf olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-105">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="1d134-106">Aşağıdaki bildirimler bir derleyici hatasına neden olur çünkü temel sınıf `BaseClass` şundan daha az erişilebilir `MyClass` :</span><span class="sxs-lookup"><span data-stu-id="1d134-106">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="1d134-107">Aşağıdaki tablo, belirtilen erişilebilirlik düzeyleri üzerindeki kısıtlamaları özetler.</span><span class="sxs-lookup"><span data-stu-id="1d134-107">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="1d134-108">Bağlam</span><span class="sxs-lookup"><span data-stu-id="1d134-108">Context</span></span>|<span data-ttu-id="1d134-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d134-109">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="1d134-110">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="1d134-110">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="1d134-111">Bir sınıf türünün doğrudan temel sınıfı en azından sınıf türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-111">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="1d134-112">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="1d134-112">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="1d134-113">Arabirim türünün açık temel arabirimleri en az arabirim türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-113">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="1d134-114">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="1d134-114">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="1d134-115">Bir temsilci türünün dönüş türü ve parametre türleri en azından temsilci türünün kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-115">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="1d134-116">Sabitler</span><span class="sxs-lookup"><span data-stu-id="1d134-116">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="1d134-117">Bir sabit türü en az sabit değer olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-117">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="1d134-118">Alanlar</span><span class="sxs-lookup"><span data-stu-id="1d134-118">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="1d134-119">Alanın türü en azından alanın kendisi kadar erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-119">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="1d134-120">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d134-120">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="1d134-121">Bir yöntemin dönüş türü ve parametre türleri en az yöntemin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-121">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="1d134-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1d134-122">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="1d134-123">Özelliğin türü en az özelliğin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-123">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="1d134-124">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="1d134-124">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="1d134-125">Bir olayın türü en az olayın kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-125">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="1d134-126">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="1d134-126">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="1d134-127">Bir dizin oluşturucunun türü ve parametre türleri en azından dizin oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-127">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="1d134-128">İşleçler</span><span class="sxs-lookup"><span data-stu-id="1d134-128">Operators</span></span>](../operators/index.md)|<span data-ttu-id="1d134-129">Bir işlecin dönüş türü ve parametre türleri en az işlecin kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-129">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="1d134-130">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="1d134-130">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="1d134-131">Bir oluşturucunun parametre türleri en az oluşturucunun kendisi olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d134-131">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="1d134-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d134-132">Example</span></span>

<span data-ttu-id="1d134-133">Aşağıdaki örnek farklı türlerin hatalı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1d134-133">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="1d134-134">Her bildirimi izleyen yorum, beklenen derleyici hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d134-134">The comment following each declaration indicates the expected compiler error.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="1d134-135">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1d134-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1d134-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d134-136">See also</span></span>

- [<span data-ttu-id="1d134-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1d134-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d134-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1d134-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d134-139">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1d134-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1d134-140">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="1d134-140">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="1d134-141">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="1d134-141">Accessibility Domain</span></span>](accessibility-domain.md)
- [<span data-ttu-id="1d134-142">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="1d134-142">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="1d134-143">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="1d134-143">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="1d134-144">genel</span><span class="sxs-lookup"><span data-stu-id="1d134-144">public</span></span>](public.md)
- [<span data-ttu-id="1d134-145">private</span><span class="sxs-lookup"><span data-stu-id="1d134-145">private</span></span>](private.md)
- [<span data-ttu-id="1d134-146">protected</span><span class="sxs-lookup"><span data-stu-id="1d134-146">protected</span></span>](protected.md)
- [<span data-ttu-id="1d134-147">internal</span><span class="sxs-lookup"><span data-stu-id="1d134-147">internal</span></span>](internal.md)
