---
title: C#Arabirimleri - Turu C# dil
description: Sözleşmeler türleri tarafından uygulanan arabirimler tanımlarC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: bfc6b59a411ff2ddb3331a8bdf24c0ae3d611273
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706409"
---
# <a name="interfaces"></a><span data-ttu-id="d424f-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d424f-103">Interfaces</span></span>

<span data-ttu-id="d424f-104">Bir ***arabirimi*** sınıfları ve yapıları tarafından uygulanan bir sözleşmeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d424f-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="d424f-105">Bir arabirim yöntemleri, özellikleri, olayları ve dizin oluşturucular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d424f-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="d424f-106">Bir arabirim tanımlar üyelerinin uygulamalarını sağlamaz; yalnızca bir sınıf ya da arabirimi uygulayan yapının tarafından sağlanması gereken üyeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d424f-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="d424f-107">, Arabirimleri görevlendirmek ***birden çok devralma***.</span><span class="sxs-lookup"><span data-stu-id="d424f-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="d424f-108">Aşağıdaki örnekte, arabirim `IComboBox` hem de devralan `ITextBox` ve `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="d424f-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="d424f-109">Sınıflar ve yapı birimleri birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="d424f-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="d424f-110">Aşağıdaki örnekte, sınıf `EditBox` hem `IControl` ve `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="d424f-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="d424f-111">Bir sınıf veya yapı, belirli bir arabirim uygular, bu sınıfın veya yapının örneği, bir arabirim türüne örtük olarak dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="d424f-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="d424f-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d424f-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="d424f-113">Dinamik tür atamaları, burada bir örnek statik olarak belirli bir arabirim uygulamak için bilinmiyor durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d424f-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="d424f-114">Örneğin, bir nesnenin elde etmek için dinamik tür atamaları aşağıdaki deyimleri kullanın `IControl` ve `IDataBound` arabirimi uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="d424f-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="d424f-115">Nesnenin çalışma zamanı gerçek türü olduğundan `EditBox`, yayınları başarılı.</span><span class="sxs-lookup"><span data-stu-id="d424f-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="d424f-116">Önceki `EditBox` sınıfı `Paint` yönteminden `IControl` arabirimi ve `Bind` yönteminden `IDataBound` arabirimi Genel üyeler kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d424f-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="d424f-117">C#aynı zamanda açık destekler ***arabirim üyesi uygulamaları***, sınıfın veya yapının üyeleri genel yapmaktan kaçınmak için etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="d424f-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="d424f-118">Açık arabirim üyesi uygulaması, tam bir arabirim üye adını kullanarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="d424f-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="d424f-119">Örneğin, `EditBox` sınıf uygulama `IControl.Paint` ve `IDataBound.Bind` yöntemlerini kullanarak açık arabirim üyesi uygulamaları gibi.</span><span class="sxs-lookup"><span data-stu-id="d424f-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="d424f-120">Açık arabirim üyeleri yalnızca arabirim türü erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d424f-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="d424f-121">Örneğin, uygulanması `IControl.Paint` tarafından önceki EditBox sınıfı yalnızca ilk dönüştürerek çağrılabilir sağlanan `EditBox` başvurusu `IControl` arabirim türü.</span><span class="sxs-lookup"><span data-stu-id="d424f-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="d424f-122">[Önceki](arrays.md)
>[İleri](enums.md)</span><span class="sxs-lookup"><span data-stu-id="d424f-122">[Previous](arrays.md)
[Next](enums.md)</span></span>