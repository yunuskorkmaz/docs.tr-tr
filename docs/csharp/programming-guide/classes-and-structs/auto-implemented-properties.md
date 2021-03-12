---
title: Otomatik uygulanan özellikler-C# Programlama Kılavuzu
description: C# ' de otomatik uygulanan bir özellik için, compteri, yalnızca özelliğin get ve set erişimcileri aracılığıyla erişilen özel, anonim bir destek alanı oluşturur.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef3e2d6dd5851801ea06d65b87c2274d8e44b4f1
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190287"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="3c0ca-103">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-103">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="3c0ca-104">C# 3,0 ve üzeri sürümlerde otomatik uygulanan özellikler, özellik erişimcilerinde ek bir mantık gerekmediği zaman özellik bildirimini daha kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-104">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="3c0ca-105">Ayrıca, istemci kodunun nesne oluşturmasını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-105">They also enable client code to create objects.</span></span> <span data-ttu-id="3c0ca-106">Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve Erişimcilerde erişilebilen özel, anonim bir destek alanı oluşturur `set` .</span><span class="sxs-lookup"><span data-stu-id="3c0ca-106">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span> <span data-ttu-id="3c0ca-107">C# 9 ve sonraki sürümlerde, `init` erişimciler otomatik olarak uygulanan özellikler olarak da bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-107">In C# 9 and later, `init` accessors can also be declared as auto-implemented properties.</span></span>
  
## <a name="example"></a><span data-ttu-id="3c0ca-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c0ca-108">Example</span></span>

<span data-ttu-id="3c0ca-109">Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="3c0ca-109">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="3c0ca-110">Arabirimlerde otomatik uygulanan özellikler bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-110">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="3c0ca-111">Otomatik uygulanan özellikler özel bir örnek yedekleme alanı bildirir ve arabirimler örnek alanlarını bildiremeyebilir.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-111">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="3c0ca-112">Bir gövde tanımlamadan bir arabirimde bir özelliği bildirmek, bu arabirimi uygulayan her bir tür tarafından uygulanması gereken erişimcilere sahip bir özellik bildirir.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-112">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="3c0ca-113">C# 6 ve üzeri sürümlerde, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3c0ca-113">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="3c0ca-114">Önceki örnekte gösterilen sınıf değişebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-114">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="3c0ca-115">İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-115">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="3c0ca-116">Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-116">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="3c0ca-117">Ancak, yalnızca bir değer kümesini (veri) kapsülleyen ve çok az davranışlara sahip olan küçük sınıflar veya yapılar için, nesneleri sabit hale getirmek üzere aşağıdaki seçeneklerden birini kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3c0ca-117">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should use one of the following options for making the objects immutable:</span></span>

* <span data-ttu-id="3c0ca-118">Yalnızca bir `get` erişimci bildirin (Oluşturucu dışında her yerde sabit).</span><span class="sxs-lookup"><span data-stu-id="3c0ca-118">Declare only a `get` accessor (immutable everywhere except the constructor).</span></span>
* <span data-ttu-id="3c0ca-119">Bir `get` erişimci ve erişimci bildirin `init` (nesne oluşturma sırasında her yerde sabit).</span><span class="sxs-lookup"><span data-stu-id="3c0ca-119">Declare a `get` accessor and an `init` accessor (immutable everywhere except during object construction).</span></span>
* <span data-ttu-id="3c0ca-120">`set`Erişimciyi [özel](../../language-reference/keywords/private.md) olarak bildirin (Sabit-müşteriler).</span><span class="sxs-lookup"><span data-stu-id="3c0ca-120">Declare the `set` accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers).</span></span>

<span data-ttu-id="3c0ca-121">Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3c0ca-121">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c0ca-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-122">See also</span></span>

- [<span data-ttu-id="3c0ca-123">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3c0ca-123">Properties</span></span>](./properties.md)
- [<span data-ttu-id="3c0ca-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="3c0ca-124">Modifiers</span></span>](../../language-reference/keywords/index.md)
