---
title: Otomatik uygulanan özellikler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 44f3beb9de8c9d339c42db26bb9c510998abc7d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597142"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="a5f49-102">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a5f49-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="a5f49-103">C# 3,0 ve sonraki sürümlerde, özellik erişimcilerinde ek bir mantık gerekmediği zaman otomatik uygulanan özellikler özellik bildirimini daha kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a5f49-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="a5f49-104">Ayrıca, istemci kodunun nesne oluşturmasını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5f49-104">They also enable client code to create objects.</span></span> <span data-ttu-id="a5f49-105">Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve `set` Erişimcilerde erişilebilen özel, anonim bir destek alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5f49-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5f49-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5f49-106">Example</span></span>  
 <span data-ttu-id="a5f49-107">Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a5f49-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 <span data-ttu-id="a5f49-108">C# 6 ve sonrasında, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a5f49-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="a5f49-109">Önceki örnekte gösterilen sınıf değişebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="a5f49-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="a5f49-110">İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a5f49-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="a5f49-111">Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5f49-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="a5f49-112">Bununla birlikte, yalnızca bir değer kümesini (veri) kapsülleyen ve hiç davranışlarına sahip olan küçük sınıflar veya yapılar için, küme erişimcisini [özel](../../language-reference/keywords/private.md) (Sabit-tüketiciler) olarak bildirerek veya yalnızca bir get bildirerek nesneleri sabit yapmalısınız. erişimci (Oluşturucu dışında her yerde sabit).</span><span class="sxs-lookup"><span data-stu-id="a5f49-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="a5f49-113">Daha fazla bilgi için [nasıl yapılır: Otomatik uygulanan özelliklerle](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)hafif bir sınıf uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a5f49-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f49-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f49-114">See also</span></span>

- [<span data-ttu-id="a5f49-115">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a5f49-115">Properties</span></span>](./properties.md)
- [<span data-ttu-id="a5f49-116">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="a5f49-116">Modifiers</span></span>](../../language-reference/keywords/modifiers.md)
