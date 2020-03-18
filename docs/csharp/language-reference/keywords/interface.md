---
title: arayüz - C# Referans
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625858"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="4440a-102">:::no-loc text="interface":::(C# Referans)</span><span class="sxs-lookup"><span data-stu-id="4440a-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="4440a-103">Arabirim bir sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4440a-103">An interface defines a contract.</span></span> <span data-ttu-id="4440a-104">Bu [`class`](class.md) [`struct`](../builtin-types/struct.md) sözleşmeyi uygulayan herhangi biri veya bu sözleşme, arabirimde tanımlanan üyelerin uygulanmasını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4440a-104">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="4440a-105">C# 8.0 ile başlayarak, bir arabirim üyeler için varsayılan bir uygulama tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="4440a-106">Ortak işlevsellik [`static`](static.md) için tek bir uygulama sağlamak için üyeleri de tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="4440a-107">Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4440a-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="4440a-108">Daha fazla bilgi ve örnekler için [Arabirimler'e](../../programming-guide/interfaces/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4440a-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="4440a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4440a-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="4440a-110">Arabirim, ad alanının veya sınıfın üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="4440a-111">Arabirim bildirimi, aşağıdaki üyelerin bildirimlerini (herhangi bir uygulama olmaksızın imzalar) içerebilir:</span><span class="sxs-lookup"><span data-stu-id="4440a-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="4440a-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4440a-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="4440a-113">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4440a-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="4440a-114">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="4440a-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="4440a-115">Olaylar</span><span class="sxs-lookup"><span data-stu-id="4440a-115">Events</span></span>](event.md)

<span data-ttu-id="4440a-116">Bu önceki üye bildirimleri genellikle bir gövde içermez.</span><span class="sxs-lookup"><span data-stu-id="4440a-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="4440a-117">C# 8.0 ile başlayarak, bir arabirim üyesi gövde bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="4440a-118">Buna varsayılan *uygulama*denir.</span><span class="sxs-lookup"><span data-stu-id="4440a-118">This is called a *default implementation*.</span></span> <span data-ttu-id="4440a-119">Gövdeleri olan üyeler, arabirimin, geçersiz bir uygulama sağlamayan sınıflar ve yapıstları için "varsayılan" bir uygulama sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4440a-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="4440a-120">Buna ek olarak, C# 8.0 ile başlayan bir arayüz şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="4440a-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="4440a-121">Sabitler</span><span class="sxs-lookup"><span data-stu-id="4440a-121">Constants</span></span>](const.md)
- [<span data-ttu-id="4440a-122">İşleçler</span><span class="sxs-lookup"><span data-stu-id="4440a-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="4440a-123">[Statik yapıcı](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="4440a-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="4440a-124">İç içe türleri</span><span class="sxs-lookup"><span data-stu-id="4440a-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="4440a-125">Statik alanlar, yöntemler, özellikler, dizinleyiciler ve olaylar</span><span class="sxs-lookup"><span data-stu-id="4440a-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="4440a-126">Açık arabirim uygulaması sözdizimini kullanan üye bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="4440a-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="4440a-127">Açık erişim değiştiriciler (varsayılan [`public`](access-modifiers.md)erişim).</span><span class="sxs-lookup"><span data-stu-id="4440a-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="4440a-128">Arabirimler örnek durumu içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="4440a-129">Statik alanlara artık izin verilirken, örnek alanlara arabirimlerde izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="4440a-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="4440a-130">[Örnek otomatik özellikler,](../../programming-guide/classes-and-structs/auto-implemented-properties.md) gizli bir alanı dolaylı olarak beyan ettikleri için arabirimlerde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4440a-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="4440a-131">Bu kuralın özellik bildirimleri üzerinde ince bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="4440a-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="4440a-132">Arabirim bildiriminde, aşağıdaki kod otomatik olarak uygulanan bir özelliği bir `class` `struct`veya .</span><span class="sxs-lookup"><span data-stu-id="4440a-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="4440a-133">Bunun yerine, varsayılan bir uygulaması olmayan ancak arabirimi uygulayan herhangi bir türde uygulanması gereken bir özellik bildirir:</span><span class="sxs-lookup"><span data-stu-id="4440a-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="4440a-134">Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="4440a-135">Bir arabirim, temel arabirimde uygulanan [bir yöntemi geçersiz kılarsa,](override.md) [açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md) sözdizimini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4440a-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="4440a-136">Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4440a-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="4440a-137">Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="4440a-138">Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="4440a-139">Buna ek olarak, varsayılan arabirim üyelerine yalnızca arabirimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="4440a-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="4440a-140">Açık arabirim uygulaması hakkında daha fazla bilgi için [bkz.](../../programming-guide/interfaces/explicit-interface-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="4440a-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="4440a-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="4440a-141">Example</span></span>

<span data-ttu-id="4440a-142">Aşağıdaki örnek, ara birim uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4440a-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="4440a-143">Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="4440a-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="4440a-144">`IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4440a-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="4440a-145">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4440a-145">C# language specification</span></span>

<span data-ttu-id="4440a-146">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Arabirimler](~/_csharplang/spec/interfaces.md) bölümüne ve Varsayılan arabirim üyeleri için özellik belirtimine bakın [- C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="4440a-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="4440a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4440a-147">See also</span></span>

- [<span data-ttu-id="4440a-148">C# Referans</span><span class="sxs-lookup"><span data-stu-id="4440a-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4440a-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4440a-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4440a-150">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="4440a-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4440a-151">Referans Türleri</span><span class="sxs-lookup"><span data-stu-id="4440a-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="4440a-152">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="4440a-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="4440a-153">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="4440a-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="4440a-154">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="4440a-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="4440a-155">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="4440a-155">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
