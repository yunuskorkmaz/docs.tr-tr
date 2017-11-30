---
title: C# arabirimleri - C# dili turu
description: "C# türleri tarafından uygulanan sözleşmeler arabirim tanımlar"
keywords: ".NET, csharp, arabirimler, birden çok devralma çok biçimlilik"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a><span data-ttu-id="b5fc0-104">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b5fc0-104">Interfaces</span></span>

<span data-ttu-id="b5fc0-105">Bir ***arabirimi*** sınıflar ve yapılar tarafından uygulanan bir sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-105">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="b5fc0-106">Arabirim yöntemleri, özellikleri, olayları ve dizin oluşturucular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-106">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="b5fc0-107">Arabirim uygulamaları tanımladığı üyelerinin sağlamaz — yalnızca bir sınıf ya da arabirimini uygulayan yapının tarafından sağlanmalıdır üyeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-107">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="b5fc0-108">Arabirimleri uygulamadığınız ***birden çok devralma***.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-108">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="b5fc0-109">Aşağıdaki örnekte, arabirim `IComboBox` hem de devralır `ITextBox` ve `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-109">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="b5fc0-110">Sınıflar ve yapılar birden çok arabirimi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-110">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="b5fc0-111">Aşağıdaki örnekte, sınıf `EditBox` her ikisi de uygulayan `IControl` ve `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-111">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="b5fc0-112">Sınıfta veya yapı belirli bir arabirimi uygulayan, o sınıfta veya yapı örnekleri, arabirim türüne örtük olarak dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-112">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="b5fc0-113">Örneğin</span><span class="sxs-lookup"><span data-stu-id="b5fc0-113">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="b5fc0-114">Dinamik tür atamaları burada örneği statik olarak belirli bir arabirim uygulamak için bilinmiyor durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-114">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="b5fc0-115">Örneğin, bir nesnenin elde etmek için dinamik tür atamaları aşağıdaki deyimleri kullanın `IControl` ve `IDataBound` arabirimi uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-115">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="b5fc0-116">Nesne çalışma zamanı gerçek tür olduğundan `EditBox`, atamaları başarılı.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-116">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="b5fc0-117">Önceki `EditBox` sınıfı, `Paint` yönteminden `IControl` arabirimi ve `Bind` yönteminden `IDataBound` arabirimi Genel üyeler kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-117">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="b5fc0-118">C# de destekler açık ***arabirim üye uygulamaları***, sınıf veya Yapı üyeleri ortak yapmaktan kaçınmak için etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-118">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="b5fc0-119">Açık arabirim üye uygulaması tam arabirimi üye adı kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-119">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="b5fc0-120">Örneğin, `EditBox` sınıf uygulama `IControl.Paint` ve `IDataBound.Bind` yöntemlerini açık kullanarak arabirimi üye uygulamaları gibi.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-120">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="b5fc0-121">Açık arabirim üyeleri yalnızca arabirim türü erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-121">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="b5fc0-122">Örneğin, uyarlamasını `IControl.Paint` tarafından önceki EditBox sınıfı yalnızca ilk dönüştürerek çağrılabilir sağlanan `EditBox` başvuru `IControl` arabirim türü.</span><span class="sxs-lookup"><span data-stu-id="b5fc0-122">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
<span data-ttu-id="b5fc0-123">[Önceki](arrays.md)
[sonraki](enums.md)</span><span class="sxs-lookup"><span data-stu-id="b5fc0-123">[Previous](arrays.md)
[Next](enums.md)</span></span>
