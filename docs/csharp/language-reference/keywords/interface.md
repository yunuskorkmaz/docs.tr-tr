---
title: arabirim-C# başvurusu
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 869f1398ae0af3c7379655aa018a9f4aacb934d7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243977"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="0f5a7-102">:::no-loc text="interface":::(C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0f5a7-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="0f5a7-103">Arabirim, bir sözleşmeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-103">An interface defines a contract.</span></span> <span data-ttu-id="0f5a7-104">[`class`](class.md) [`struct`](../builtin-types/struct.md) Bu sözleşmeyi uygulayan her türlü veya, arabirimde tanımlanan üyelerin bir uygulamasını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-104">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="0f5a7-105">C# 8,0 ' den başlayarak bir arabirim, Üyeler için varsayılan bir uygulama tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="0f5a7-106">Ayrıca, [`static`](static.md) ortak işlevlere yönelik tek bir uygulama sağlamak için üyeleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="0f5a7-107">Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="0f5a7-108">Daha fazla bilgi ve örnek için bkz. [arabirimler](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="0f5a7-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f5a7-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f5a7-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="0f5a7-110">Arabirim, bir ad alanı veya sınıf üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="0f5a7-111">Arabirim bildirimi, aşağıdaki üyelerin bildirimlerini (herhangi bir uygulama olmadan imzalar) içerebilir:</span><span class="sxs-lookup"><span data-stu-id="0f5a7-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="0f5a7-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f5a7-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="0f5a7-113">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0f5a7-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="0f5a7-114">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0f5a7-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="0f5a7-115">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="0f5a7-115">Events</span></span>](event.md)

<span data-ttu-id="0f5a7-116">Bu önceki üye bildirimleri genellikle gövde içermez.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="0f5a7-117">C# 8,0 ' den başlayarak bir arabirim üyesi bir gövde bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="0f5a7-118">Bu, varsayılan bir *uygulama*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-118">This is called a *default implementation*.</span></span> <span data-ttu-id="0f5a7-119">Gövdeler içeren Üyeler, arabirimin geçersiz kılan bir uygulama sağlamayan sınıflar ve yapılar için "varsayılan" bir uygulama sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="0f5a7-120">Buna ek olarak, C# 8,0 ' den itibaren bir arabirim şunlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="0f5a7-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="0f5a7-121">Sabitler</span><span class="sxs-lookup"><span data-stu-id="0f5a7-121">Constants</span></span>](const.md)
- [<span data-ttu-id="0f5a7-122">İşleçler</span><span class="sxs-lookup"><span data-stu-id="0f5a7-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="0f5a7-123">[Statik Oluşturucu](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="0f5a7-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="0f5a7-124">İç içe türler</span><span class="sxs-lookup"><span data-stu-id="0f5a7-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="0f5a7-125">Statik alanlar, Yöntemler, özellikler, Dizin oluşturucular ve olaylar</span><span class="sxs-lookup"><span data-stu-id="0f5a7-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="0f5a7-126">Açık arabirim uygulama sözdizimini kullanan üye bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="0f5a7-127">Açık erişim değiştiricileri (varsayılan erişim [`public`](access-modifiers.md) ).</span><span class="sxs-lookup"><span data-stu-id="0f5a7-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="0f5a7-128">Arabirimler örnek durumu içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="0f5a7-129">Statik alanlara artık izin verildiğinde, arabirimlerde örnek alanlarına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="0f5a7-130">[Örnek otomatik Özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) , açıkça gizli bir alan bildirdiklerinde arabirimlerde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="0f5a7-131">Bu kuralın Özellik bildirimlerinde hafif bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="0f5a7-132">Bir arabirim bildiriminde, aşağıdaki kod bir veya içinde olduğu gibi otomatik uygulanan bir özellik bildirmiyor `class` `struct` .</span><span class="sxs-lookup"><span data-stu-id="0f5a7-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="0f5a7-133">Bunun yerine, varsayılan bir uygulamasına sahip olmayan ancak arabirimini uygulayan herhangi bir türde uygulanması gereken bir özellik bildirir:</span><span class="sxs-lookup"><span data-stu-id="0f5a7-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="0f5a7-134">Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="0f5a7-135">Bir arabirim Temel arabirimde uygulanan [bir yöntemi geçersiz kıldığında](override.md) , [Açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md) söz dizimini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="0f5a7-136">Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="0f5a7-137">Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="0f5a7-138">Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="0f5a7-139">Ayrıca, varsayılan arabirim üyelerine yalnızca arabirimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="0f5a7-140">Açık arabirim uygulama hakkında daha fazla bilgi için bkz. [Açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="0f5a7-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f5a7-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f5a7-141">Example</span></span>

<span data-ttu-id="0f5a7-142">Aşağıdaki örnek, ara birim uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="0f5a7-143">Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="0f5a7-144">`IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="0f5a7-145">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0f5a7-145">C# language specification</span></span>

<span data-ttu-id="0f5a7-146">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [arabirimler](~/_csharplang/spec/interfaces.md) bölümüne ve varsayılan arabirim üyeleri için özellik belirtimine bakın [-C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="0f5a7-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="0f5a7-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f5a7-147">See also</span></span>

- [<span data-ttu-id="0f5a7-148">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0f5a7-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0f5a7-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0f5a7-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0f5a7-150">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0f5a7-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0f5a7-151">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="0f5a7-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="0f5a7-152">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="0f5a7-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="0f5a7-153">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="0f5a7-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="0f5a7-154">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="0f5a7-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
