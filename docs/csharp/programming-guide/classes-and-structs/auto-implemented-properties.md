---
title: Otomatik uygulanan Özellikler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: b5447dea8b510def95041549555de2ed5592e2d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683762"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="76811-102">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="76811-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="76811-103">İlave bir mantık özellik gerektiğinde C# 3.0 ve sonraki sürümlerinde, otomatik uygulanan özellikler özellik bildirimini daha kısa yapın.</span><span class="sxs-lookup"><span data-stu-id="76811-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="76811-104">Nesneleri oluşturmak istemci kodu aynı zamanda tanırlar.</span><span class="sxs-lookup"><span data-stu-id="76811-104">They also enable client code to create objects.</span></span> <span data-ttu-id="76811-105">Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin erişilebilen özel, anonim destek alanı oluşturur `get` ve `set` erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="76811-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76811-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="76811-106">Example</span></span>  
 <span data-ttu-id="76811-107">Aşağıdaki örnek, bazı otomatik uygulanan özellikler sahip basit bir sınıfı gösterir:</span><span class="sxs-lookup"><span data-stu-id="76811-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 <span data-ttu-id="76811-108">C# 6 ve sonraki sürümlerinde, otomatik uygulanan özellikler alanları için benzer şekilde başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76811-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="76811-109">Önceki örnekte gösterilen sınıf değişebilir.</span><span class="sxs-lookup"><span data-stu-id="76811-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="76811-110">Oluşturulduktan sonra istemci kodu nesne değerleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76811-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="76811-111">Önemli davranışı (yöntem) yanı sıra veri içeren karmaşık sınıflarda ortak özellikler sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="76811-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="76811-112">Ancak, küçük sınıfları veya çok az kayıpla veya hiç davranışları yalnızca (veriler), bir dizi kapsüllemek ve yapı birimleri için ya da nesneleri sabit olarak ayarlama erişimcisine bildirerek yaptığınız [özel](../../../csharp/language-reference/keywords/private.md) (tüketicilere değişmez) ya da yalnızca bir alma erişimcisi (oluşturucu dışında her yerde değişmez) bildirme.</span><span class="sxs-lookup"><span data-stu-id="76811-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="76811-113">Daha fazla bilgi için [nasıl yapılır: Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="76811-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76811-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76811-114">See also</span></span>

- [<span data-ttu-id="76811-115">Özellikler</span><span class="sxs-lookup"><span data-stu-id="76811-115">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="76811-116">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="76811-116">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
