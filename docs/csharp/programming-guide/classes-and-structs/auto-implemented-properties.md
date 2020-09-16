---
title: Otomatik uygulanan özellikler-C# Programlama Kılavuzu
description: C# ' de otomatik uygulanan bir özellik için, compteri, yalnızca özelliğin get ve set erişimcileri aracılığıyla erişilen özel, anonim bir destek alanı oluşturur.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 72f774d84266292412be9b954fc206debc8ac55e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555906"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="4bf33-103">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4bf33-103">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="4bf33-104">C# 3,0 ve üzeri sürümlerde otomatik uygulanan özellikler, özellik erişimcilerinde ek bir mantık gerekmediği zaman özellik bildirimini daha kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4bf33-104">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="4bf33-105">Ayrıca, istemci kodunun nesne oluşturmasını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bf33-105">They also enable client code to create objects.</span></span> <span data-ttu-id="4bf33-106">Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve Erişimcilerde erişilebilen özel, anonim bir destek alanı oluşturur `set` .</span><span class="sxs-lookup"><span data-stu-id="4bf33-106">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="4bf33-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bf33-107">Example</span></span>

<span data-ttu-id="4bf33-108">Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="4bf33-108">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="4bf33-109">Arabirimlerde otomatik uygulanan özellikler bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bf33-109">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="4bf33-110">Otomatik uygulanan özellikler özel bir örnek yedekleme alanı bildirir ve arabirimler örnek alanlarını bildiremeyebilir.</span><span class="sxs-lookup"><span data-stu-id="4bf33-110">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="4bf33-111">Bir gövde tanımlamadan bir arabirimde bir özelliği bildirmek, bu arabirimi uygulayan her bir tür tarafından uygulanması gereken erişimcilere sahip bir özellik bildirir.</span><span class="sxs-lookup"><span data-stu-id="4bf33-111">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="4bf33-112">C# 6 ve üzeri sürümlerde, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4bf33-112">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="4bf33-113">Önceki örnekte gösterilen sınıf değişebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="4bf33-113">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="4bf33-114">İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4bf33-114">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="4bf33-115">Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4bf33-115">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="4bf33-116">Bununla birlikte, yalnızca bir değer kümesini (veri) kapsülleyen ve hiç davranışlarına sahip olan küçük sınıflar veya yapılar için, küme erişimcisini [Private](../../language-reference/keywords/private.md) (Sabit-tüketiciler) olarak bildirerek veya yalnızca bir get erişimcisi bildirerek (Oluşturucu dışında sabit olarak) nesneleri sabit hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bf33-116">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="4bf33-117">Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4bf33-117">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4bf33-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bf33-118">See also</span></span>

- [<span data-ttu-id="4bf33-119">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4bf33-119">Properties</span></span>](./properties.md)
- [<span data-ttu-id="4bf33-120">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="4bf33-120">Modifiers</span></span>](../../language-reference/keywords/index.md)
