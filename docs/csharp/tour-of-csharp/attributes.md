---
title: "C# öznitelikleri - C# dili turu"
description: "Öznitelikleri C# kullanarak bildirim temelli programlama hakkında bilgi edinin"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 6878a408ef892ee47a03bfa04f736b9bf9671696
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="attributes"></a><span data-ttu-id="1ff03-104">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ff03-104">Attributes</span></span>

<span data-ttu-id="1ff03-105">Türleri, üyeleri ve diğer varlıklar bir C# programında davranışlarını belirli yönlerini denetlemek değiştiricileri destekler.</span><span class="sxs-lookup"><span data-stu-id="1ff03-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="1ff03-106">Örneğin, bir yöntemin erişilebilirliğini kullanılarak denetlenir `public`, `protected`, `internal`, ve `private` değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="1ff03-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="1ff03-107">Kullanıcı tanımlı tür tanımlayıcı bilgiler program varlıklara bağlı ve çalışma zamanında alınır, C# Bu yetenek genelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1ff03-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="1ff03-108">Programları belirtin Bu ek tanımlayıcı bilgiler tanımlama ve kullanma ***öznitelikleri***.</span><span class="sxs-lookup"><span data-stu-id="1ff03-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="1ff03-109">Aşağıdaki örnek bildiren bir `HelpAttribute` , ilişkili belgelere bağlantılar sağlamak için program varlıklar üzerinde yerleştirilebilir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1ff03-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="1ff03-110">Tüm öznitelik sınıfları türetin <xref:System.Attribute> temel standart kitaplığı tarafından sağlanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1ff03-110">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="1ff03-111">Öznitelikler, tüm bağımsız değişkenleri köşeli ayraç içinde ilişkili bildirimi hemen önce yanı sıra bunların adı vererek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1ff03-111">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="1ff03-112">Bir özniteliğin adı biterse `Attribute`, öznitelik başvurulduğunda adı kısmı atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1ff03-112">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="1ff03-113">Örneğin, `HelpAttribute` özniteliği şu şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ff03-113">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="1ff03-114">Bu örnek iliştirir bir `HelpAttribute` için `Widget` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1ff03-114">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="1ff03-115">Başka bir ekler `HelpAttribute` için `Display` sınıfında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1ff03-115">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="1ff03-116">Genel oluşturucular öznitelik sınıfı, öznitelik için bir program varlığı iliştirildiğinde sağlanmalıdır bilgileri denetler.</span><span class="sxs-lookup"><span data-stu-id="1ff03-116">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="1ff03-117">Ek bilgi öznitelik sınıfı ortak okuma-yazma özelliklerini başvurarak sağlanabilir (referansı gibi `Topic` özelliği daha önce).</span><span class="sxs-lookup"><span data-stu-id="1ff03-117">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="1ff03-118">Yansıma yoluyla belirli bir öznitelik istendiğinde, program kaynağında sağlanan bilgileri ile öznitelik sınıfı oluşturucusu çağrılır ve sonuçta elde edilen özniteliği örneği döndürdü.</span><span class="sxs-lookup"><span data-stu-id="1ff03-118">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="1ff03-119">Ek bilgi özelliklerinden verdiyse, öznitelik örneği döndürülmeden önce bu özellikleri belirtilen değerlere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1ff03-119">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="1ff03-120">Önceki</span><span class="sxs-lookup"><span data-stu-id="1ff03-120">Previous</span></span>](delegates.md)
