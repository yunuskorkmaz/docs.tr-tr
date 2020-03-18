---
title: C# Arayüzler - C# dilinde bir tur
description: "Arabirimler C'deki türlere göre uygulanan sözleşmeleri tanımlar #"
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159136"
---
# <a name="interfaces"></a><span data-ttu-id="d1121-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d1121-103">Interfaces</span></span>

<span data-ttu-id="d1121-104">***Arabirim,*** sınıflar ve structs tarafından uygulanabilen bir sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1121-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="d1121-105">Arabirim yöntemleri, özellikleri, olayları ve dizinleyicileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d1121-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="d1121-106">Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz, yalnızca arabirimi uygulayan sınıflar veya yapıstları tarafından sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1121-106">An interface doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="d1121-107">Arabirimler ***birden çok devralma***istihdam edebilir.</span><span class="sxs-lookup"><span data-stu-id="d1121-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="d1121-108">Aşağıdaki örnekte, arabirim `IComboBox` her `ITextBox` ikisinden ve `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="d1121-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="d1121-109">Sınıflar ve structs birden çok arabirim uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1121-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="d1121-110">Aşağıdaki örnekte, sınıf `EditBox` hem `IControl` ve `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="d1121-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="d1121-111">Bir sınıf veya yapı belirli bir arabirimi uyguladığında, o sınıfın veya yapının örnekleri örtülü olarak bu arabirim türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="d1121-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="d1121-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d1121-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="d1121-113">Bir örneğin belirli bir arabirimi uygulamak için statik olarak bilinmediği durumlarda, dinamik tür dökümleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1121-113">In cases where an instance isn't statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="d1121-114">Örneğin, aşağıdaki ifadeler bir nesnenin `IControl` ve `IDataBound` arabirim uygulamalarını elde etmek için dinamik tür dökümleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1121-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="d1121-115">Nesnenin çalışma zamanı gerçek türü `EditBox`olduğundan, dökümler başarılı dır.</span><span class="sxs-lookup"><span data-stu-id="d1121-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="d1121-116">Önceki `EditBox` `Paint` sınıfta, `IControl` arabirimden gelen `Bind` yöntem ve `IDataBound` arabirimden gelen yöntem ortak üyeler kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d1121-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="d1121-117">C# ayrıca açık ***arabirim üyesi uygulamalarını***da destekler ve üyeleri herkese açık hale getirmemek için sınıfın veya yapının kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1121-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="d1121-118">Açık bir arayüz üye uygulaması tam nitelikli arabirim üye adı kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="d1121-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="d1121-119">Örneğin, `EditBox` sınıf `IControl.Paint` ve `IDataBound.Bind` yöntemleri aşağıdaki gibi açık arabirim üye uygulamalarını kullanarak uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="d1121-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="d1121-120">Açık arabirim üyelerine yalnızca arabirim türünden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1121-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="d1121-121">Örneğin, önceki EditBox sınıfı tarafından `IControl.Paint` sağlanan uygulama yalnızca ilk `EditBox` `IControl` olarak başvuruyu arabirim türüne dönüştürerek çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1121-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="d1121-122">[Önceki](arrays.md)
>[Sonraki](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="d1121-122">[Previous](arrays.md)
[Next](delegates.md)</span></span>
