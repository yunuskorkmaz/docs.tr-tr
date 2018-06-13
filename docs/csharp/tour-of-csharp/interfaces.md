---
title: C# arabirimleri - C# dili turu
description: C# türleri tarafından uygulanan sözleşmeler arabirim tanımlar
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 0ad02d5b2792656783d93b2cc767aeb81efbc30e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343902"
---
# <a name="interfaces"></a><span data-ttu-id="c5925-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="c5925-103">Interfaces</span></span>

<span data-ttu-id="c5925-104">Bir ***arabirimi*** sınıflar ve yapılar tarafından uygulanan bir sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5925-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="c5925-105">Arabirim yöntemleri, özellikleri, olayları ve dizin oluşturucular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5925-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="c5925-106">Arabirim uygulamaları tanımladığı üyelerinin sağlamaz — yalnızca bir sınıf ya da arabirimini uygulayan yapının tarafından sağlanmalıdır üyeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5925-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="c5925-107">Arabirimleri uygulamadığınız ***birden çok devralma***.</span><span class="sxs-lookup"><span data-stu-id="c5925-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="c5925-108">Aşağıdaki örnekte, arabirim `IComboBox` hem de devralır `ITextBox` ve `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="c5925-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="c5925-109">Sınıflar ve yapılar birden çok arabirimi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5925-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="c5925-110">Aşağıdaki örnekte, sınıf `EditBox` her ikisi de uygulayan `IControl` ve `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="c5925-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="c5925-111">Sınıfta veya yapı belirli bir arabirimi uygulayan, o sınıfta veya yapı örnekleri, arabirim türüne örtük olarak dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="c5925-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="c5925-112">Örneğin</span><span class="sxs-lookup"><span data-stu-id="c5925-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="c5925-113">Dinamik tür atamaları burada örneği statik olarak belirli bir arabirim uygulamak için bilinmiyor durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5925-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="c5925-114">Örneğin, bir nesnenin elde etmek için dinamik tür atamaları aşağıdaki deyimleri kullanın `IControl` ve `IDataBound` arabirimi uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="c5925-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="c5925-115">Nesne çalışma zamanı gerçek tür olduğundan `EditBox`, atamaları başarılı.</span><span class="sxs-lookup"><span data-stu-id="c5925-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="c5925-116">Önceki `EditBox` sınıfı, `Paint` yönteminden `IControl` arabirimi ve `Bind` yönteminden `IDataBound` arabirimi Genel üyeler kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c5925-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="c5925-117">C# de destekler açık ***arabirim üye uygulamaları***, sınıf veya Yapı üyeleri ortak yapmaktan kaçınmak için etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="c5925-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="c5925-118">Açık arabirim üye uygulaması tam arabirimi üye adı kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="c5925-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="c5925-119">Örneğin, `EditBox` sınıf uygulama `IControl.Paint` ve `IDataBound.Bind` yöntemlerini açık kullanarak arabirimi üye uygulamaları gibi.</span><span class="sxs-lookup"><span data-stu-id="c5925-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="c5925-120">Açık arabirim üyeleri yalnızca arabirim türü erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5925-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="c5925-121">Örneğin, uyarlamasını `IControl.Paint` tarafından önceki EditBox sınıfı yalnızca ilk dönüştürerek çağrılabilir sağlanan `EditBox` başvuru `IControl` arabirim türü.</span><span class="sxs-lookup"><span data-stu-id="c5925-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
<span data-ttu-id="c5925-122">[Önceki](arrays.md)
[sonraki](enums.md)</span><span class="sxs-lookup"><span data-stu-id="c5925-122">[Previous](arrays.md)
[Next](enums.md)</span></span>
