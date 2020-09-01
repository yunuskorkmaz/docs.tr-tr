---
description: ':::no-loc text=interface::: (C# Başvurusu)'
title: arabirim-C# başvurusu
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134594"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="6c3fd-103">:::no-loc text="interface"::: (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6c3fd-103">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="6c3fd-104">Arabirim, bir sözleşmeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-104">An interface defines a contract.</span></span> <span data-ttu-id="6c3fd-105">[`class`](class.md) [`struct`](../builtin-types/struct.md) Bu sözleşmeyi uygulayan her türlü veya, arabirimde tanımlanan üyelerin bir uygulamasını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-105">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="6c3fd-106">C# 8,0 ' den başlayarak bir arabirim, Üyeler için varsayılan bir uygulama tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-106">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="6c3fd-107">Ayrıca, [`static`](static.md) ortak işlevlere yönelik tek bir uygulama sağlamak için üyeleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-107">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="6c3fd-108">Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-108">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="6c3fd-109">Daha fazla bilgi ve örnek için bkz. [arabirimler](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c3fd-109">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="6c3fd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c3fd-110">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="6c3fd-111">Arabirim, bir ad alanı veya sınıf üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-111">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="6c3fd-112">Arabirim bildirimi, aşağıdaki üyelerin bildirimlerini (herhangi bir uygulama olmadan imzalar) içerebilir:</span><span class="sxs-lookup"><span data-stu-id="6c3fd-112">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="6c3fd-113">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6c3fd-113">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="6c3fd-114">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6c3fd-114">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="6c3fd-115">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="6c3fd-115">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="6c3fd-116">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="6c3fd-116">Events</span></span>](event.md)

<span data-ttu-id="6c3fd-117">Bu önceki üye bildirimleri genellikle gövde içermez.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-117">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="6c3fd-118">C# 8,0 ' den başlayarak bir arabirim üyesi bir gövde bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-118">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="6c3fd-119">Bu, varsayılan bir *uygulama*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-119">This is called a *default implementation*.</span></span> <span data-ttu-id="6c3fd-120">Gövdeler içeren Üyeler, arabirimin geçersiz kılan bir uygulama sağlamayan sınıflar ve yapılar için "varsayılan" bir uygulama sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-120">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="6c3fd-121">Buna ek olarak, C# 8,0 ' den itibaren bir arabirim şunlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="6c3fd-121">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="6c3fd-122">Sabitler</span><span class="sxs-lookup"><span data-stu-id="6c3fd-122">Constants</span></span>](const.md)
- [<span data-ttu-id="6c3fd-123">İşleçler</span><span class="sxs-lookup"><span data-stu-id="6c3fd-123">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="6c3fd-124">[Statik Oluşturucu](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="6c3fd-124">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="6c3fd-125">İç içe türler</span><span class="sxs-lookup"><span data-stu-id="6c3fd-125">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="6c3fd-126">Statik alanlar, Yöntemler, özellikler, Dizin oluşturucular ve olaylar</span><span class="sxs-lookup"><span data-stu-id="6c3fd-126">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="6c3fd-127">Açık arabirim uygulama sözdizimini kullanan üye bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-127">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="6c3fd-128">Açık erişim değiştiricileri (varsayılan erişim [`public`](access-modifiers.md) ).</span><span class="sxs-lookup"><span data-stu-id="6c3fd-128">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="6c3fd-129">Arabirimler örnek durumu içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-129">Interfaces may not contain instance state.</span></span> <span data-ttu-id="6c3fd-130">Statik alanlara artık izin verildiğinde, arabirimlerde örnek alanlarına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-130">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="6c3fd-131">[Örnek otomatik Özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) , açıkça gizli bir alan bildirdiklerinde arabirimlerde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-131">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="6c3fd-132">Bu kuralın Özellik bildirimlerinde hafif bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-132">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="6c3fd-133">Bir arabirim bildiriminde, aşağıdaki kod bir veya içinde olduğu gibi otomatik uygulanan bir özellik bildirmiyor `class` `struct` .</span><span class="sxs-lookup"><span data-stu-id="6c3fd-133">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="6c3fd-134">Bunun yerine, varsayılan bir uygulamasına sahip olmayan ancak arabirimini uygulayan herhangi bir türde uygulanması gereken bir özellik bildirir:</span><span class="sxs-lookup"><span data-stu-id="6c3fd-134">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="6c3fd-135">Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-135">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="6c3fd-136">Bir arabirim Temel arabirimde uygulanan [bir yöntemi geçersiz kıldığında](override.md) , [Açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md) söz dizimini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-136">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="6c3fd-137">Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-137">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="6c3fd-138">Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-138">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="6c3fd-139">Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-139">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="6c3fd-140">Ayrıca, varsayılan arabirim üyelerine yalnızca arabirimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-140">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="6c3fd-141">Açık arabirim uygulama hakkında daha fazla bilgi için bkz. [Açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="6c3fd-141">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="6c3fd-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c3fd-142">Example</span></span>

<span data-ttu-id="6c3fd-143">Aşağıdaki örnek, ara birim uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-143">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="6c3fd-144">Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-144">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="6c3fd-145">`IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-145">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="6c3fd-146">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6c3fd-146">C# language specification</span></span>

<span data-ttu-id="6c3fd-147">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [arabirimler](~/_csharplang/spec/interfaces.md) bölümüne ve varsayılan arabirim üyeleri için özellik belirtimine bakın [-C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="6c3fd-147">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="6c3fd-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c3fd-148">See also</span></span>

- [<span data-ttu-id="6c3fd-149">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6c3fd-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6c3fd-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6c3fd-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6c3fd-151">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6c3fd-151">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6c3fd-152">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="6c3fd-152">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="6c3fd-153">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6c3fd-153">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="6c3fd-154">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="6c3fd-154">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="6c3fd-155">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="6c3fd-155">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
