---
title: interface (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253817"
---
# <a name="interface-c-reference"></a><span data-ttu-id="adeb0-102">interface (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="adeb0-102">interface (C# Reference)</span></span>

<span data-ttu-id="adeb0-103">Bir arabirim yalnızca ait imzaları içerir [yöntemleri](../../programming-guide/classes-and-structs/methods.md), [özellikleri](../../programming-guide/classes-and-structs/properties.md), [olayları](../../programming-guide/events/index.md) veya [dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="adeb0-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="adeb0-104">Ara birimi uygulayan bir sınıfın veya yapının, ara birim tanımında belirtilen ara birim üyelerini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="adeb0-105">Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="adeb0-106">Daha fazla bilgi ve örnekler için bkz. [arabirimleri](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="adeb0-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="adeb0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="adeb0-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="adeb0-108">Ara birim, bir ad alanının veya bir sınıfın üyesi olabilir ve aşağıdaki üyelerin imzalarını içerebilir:</span><span class="sxs-lookup"><span data-stu-id="adeb0-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="adeb0-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="adeb0-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="adeb0-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="adeb0-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="adeb0-111">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="adeb0-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="adeb0-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="adeb0-112">Events</span></span>](event.md)

<span data-ttu-id="adeb0-113">Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="adeb0-114">Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="adeb0-115">Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="adeb0-116">Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="adeb0-117">Daha fazla ayrıntı ve kod örnekleri açık arabirim uygulaması üzerinde görmek [açık arabirim uygulaması](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="adeb0-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="adeb0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="adeb0-118">Example</span></span>

<span data-ttu-id="adeb0-119">Aşağıdaki örnek, ara birim uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="adeb0-120">Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="adeb0-121">`IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="adeb0-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="adeb0-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="adeb0-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="adeb0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adeb0-123">See also</span></span>

- [<span data-ttu-id="adeb0-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="adeb0-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="adeb0-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="adeb0-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="adeb0-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="adeb0-126">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="adeb0-127">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="adeb0-127">Reference Types</span></span>](reference-types.md)  
- [<span data-ttu-id="adeb0-128">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="adeb0-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)  
- [<span data-ttu-id="adeb0-129">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="adeb0-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)  
- [<span data-ttu-id="adeb0-130">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="adeb0-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)  
- [<span data-ttu-id="adeb0-131">class</span><span class="sxs-lookup"><span data-stu-id="adeb0-131">class</span></span>](class.md)  
- [<span data-ttu-id="adeb0-132">struct</span><span class="sxs-lookup"><span data-stu-id="adeb0-132">struct</span></span>](struct.md)  
- [<span data-ttu-id="adeb0-133">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="adeb0-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
