---
title: "Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1aa923c6d8208c2d5451957c4112493d0acd561d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="6dfba-102">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6dfba-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="6dfba-103">İlave bir mantık özellik gerektiğinde C# 3.0 ve sonraki sürümlerinde, otomatik uygulanan özellikler özellik bildirimi daha kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6dfba-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="6dfba-104">Bunlar ayrıca nesneleri oluşturmak istemci kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="6dfba-104">They also enable client code to create objects.</span></span> <span data-ttu-id="6dfba-105">Aşağıdaki örnekte gösterildiği gibi bir özelliği bildirme, derleyici özelliğin yalnızca erişilebilir bir özel, anonim yedekleme alanını oluşturur `get` ve `set` erişimciler.</span><span class="sxs-lookup"><span data-stu-id="6dfba-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dfba-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6dfba-106">Example</span></span>  
 <span data-ttu-id="6dfba-107">Aşağıdaki örnek, bazı otomatik uygulanan özellikler olan basit bir sınıfı gösterir:</span><span class="sxs-lookup"><span data-stu-id="6dfba-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="6dfba-108">C# 6 ve üzeri, otomatik uygulanan özellikler benzer şekilde alanlara başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6dfba-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="6dfba-109">Önceki örnekte gösterilen sınıfı değişebilir.</span><span class="sxs-lookup"><span data-stu-id="6dfba-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="6dfba-110">Oluşturulduktan sonra istemci kodu nesnelerindeki değerleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dfba-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="6dfba-111">Veri yanı sıra önemli davranışları (yöntemleri) içeren karmaşık sınıflarda ortak özellikler sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6dfba-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="6dfba-112">Ancak, küçük sınıf ya da yalnızca bir değer (veri) kümesini kapsüllemek ve çok az kayıpla veya hiç davranışları yapının için ya da nesneleri değişmez olarak set erişimcisi bildirerek yaptığınız [özel](../../../csharp/language-reference/keywords/private.md) (tüketiciye değişmez) ya da yalnızca bir get erişimcisine (değişmez Oluşturucusu dışında her yerde) bildirme.</span><span class="sxs-lookup"><span data-stu-id="6dfba-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="6dfba-113">Daha fazla bilgi için bkz: [nasıl yapılır: Auto-Implemented özelliklerle hafif bir sınıf uygulama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6dfba-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="6dfba-114">Bu kaynak kodunuzdan erişilebilir olmadığından öznitelikleri otomatik uygulanan özellikler ancak yedekleme alanları üzerinde açıkça izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6dfba-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="6dfba-115">Öznitelik bir özelliğin yedekleme alanı kullanmanız gerekiyorsa, yalnızca normal bir özellik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6dfba-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfba-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6dfba-116">See Also</span></span>  
 [<span data-ttu-id="6dfba-117">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="6dfba-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="6dfba-118">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="6dfba-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
