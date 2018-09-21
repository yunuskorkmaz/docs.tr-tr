---
title: Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 0d32dfd626cb8484e935dd0e8608c2e29d3ecbde
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478272"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="95ade-102">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="95ade-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="95ade-103">İlave bir mantık özellik gerektiğinde C# 3.0 ve sonraki sürümlerinde, otomatik uygulanan özellikler özellik bildirimini daha kısa yapın.</span><span class="sxs-lookup"><span data-stu-id="95ade-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="95ade-104">Nesneleri oluşturmak istemci kodu aynı zamanda tanırlar.</span><span class="sxs-lookup"><span data-stu-id="95ade-104">They also enable client code to create objects.</span></span> <span data-ttu-id="95ade-105">Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin erişilebilen özel, anonim destek alanı oluşturur `get` ve `set` erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="95ade-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95ade-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="95ade-106">Example</span></span>  
 <span data-ttu-id="95ade-107">Aşağıdaki örnek, bazı otomatik uygulanan özellikler sahip basit bir sınıfı gösterir:</span><span class="sxs-lookup"><span data-stu-id="95ade-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="95ade-108">C# 6 ve sonraki sürümlerinde, otomatik uygulanan özellikler alanları için benzer şekilde başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="95ade-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="95ade-109">Önceki örnekte gösterilen sınıf değişebilir.</span><span class="sxs-lookup"><span data-stu-id="95ade-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="95ade-110">Oluşturulduktan sonra istemci kodu nesne değerleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95ade-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="95ade-111">Önemli davranışı (yöntem) yanı sıra veri içeren karmaşık sınıflarda ortak özellikler sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="95ade-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="95ade-112">Ancak, küçük sınıfları veya çok az kayıpla veya hiç davranışları yalnızca (veriler), bir dizi kapsüllemek ve yapı birimleri için ya da nesneleri sabit olarak ayarlama erişimcisine bildirerek yaptığınız [özel](../../../csharp/language-reference/keywords/private.md) (tüketicilere değişmez) ya da yalnızca bir alma erişimcisi (oluşturucu dışında her yerde değişmez) bildirme.</span><span class="sxs-lookup"><span data-stu-id="95ade-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="95ade-113">Daha fazla bilgi için [nasıl yapılır: bir basit sınıf Implemented Properties ile uygulama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="95ade-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="95ade-114">Bu kaynak kodunuzdan erişilebilir olmadığından öznitelikleri otomatik uygulanan özellikler ancak açıkça destekleyen alanlar izin verilir.</span><span class="sxs-lookup"><span data-stu-id="95ade-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="95ade-115">Bir öznitelik özelliğinin destek alanı üzerinde kullanmanız gerekirse, normal bir özellik oluşturmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="95ade-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ade-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95ade-116">See Also</span></span>

- [<span data-ttu-id="95ade-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="95ade-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="95ade-118">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="95ade-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
