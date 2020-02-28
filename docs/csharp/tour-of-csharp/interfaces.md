---
title: C#Arabirimler- C# dilin turu
description: İçindeki türler tarafından uygulanan sözleşmeleri tanımlayan arabirimlerC#
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159136"
---
# <a name="interfaces"></a><span data-ttu-id="b6ba1-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b6ba1-103">Interfaces</span></span>

<span data-ttu-id="b6ba1-104">***Arabirim*** , sınıflar ve yapılar tarafından uygulanabilecek bir sözleşmeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="b6ba1-105">Arabirim, Yöntemler, özellikler, olaylar ve Dizin oluşturucular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="b6ba1-106">Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz; yalnızca arabirimini uygulayan sınıflar veya yapılar tarafından sağlanması gereken üyeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-106">An interface doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="b6ba1-107">Arabirimler ***birden fazla devralma***kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="b6ba1-108">Aşağıdaki örnekte, arabirimi `IComboBox` `ITextBox` ve `IListBox`devralır.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="b6ba1-109">Sınıflar ve yapılar birden çok arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="b6ba1-110">Aşağıdaki örnekte, sınıfı `EditBox` hem `IControl` hem de `IDataBound`uygular.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="b6ba1-111">Bir sınıf veya yapı belirli bir arabirimi uygularsa, bu sınıfın veya yapının örnekleri örtülü olarak bu arabirim türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="b6ba1-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b6ba1-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="b6ba1-113">Bir örneğin belirli bir arabirimi uygulamak için statik olarak bilinen bir durum olduğu durumlarda, dinamik tür atamaları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-113">In cases where an instance isn't statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="b6ba1-114">Örneğin, aşağıdaki deyimler bir nesnenin `IControl` ve `IDataBound` arabirim uygulamalarını almak için dinamik tür yayınları kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="b6ba1-115">Nesnenin çalışma zamanı gerçek türü `EditBox`olduğundan, yayınlar başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="b6ba1-116">Önceki `EditBox` sınıfında, `IControl` arabiriminden `Paint` yöntemi ve `IDataBound` arabirimindeki `Bind` yöntemi ortak Üyeler kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="b6ba1-117">C#Ayrıca, açık ***arabirim üye uygulamalarını***destekler, bu sayede, üyeleri genel hale getirmeyi önlemek için sınıfı veya yapıyı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="b6ba1-118">Açık arabirim üyesi uygulama, tam nitelikli arabirim üye adı kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="b6ba1-119">Örneğin `EditBox` sınıfı, aşağıdaki gibi açık arabirim üye uygulamalarını kullanarak `IControl.Paint` ve `IDataBound.Bind` yöntemlerini uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="b6ba1-120">Açık arabirim üyelerine yalnızca arabirim türü aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="b6ba1-121">Örneğin, önceki EditBox sınıfı tarafından sunulan `IControl.Paint` uygulanması yalnızca `IControl` arabirimi türüne `EditBox` başvurusu dönüştürülürken çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ba1-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="b6ba1-122">[Önceki](arrays.md)
>[İleri](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="b6ba1-122">[Previous](arrays.md)
[Next](delegates.md)</span></span>
