---
title: Otomatik Uygulanan Özellikler - C# Programlama Kılavuzu
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170331"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="fdd46-102">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fdd46-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="fdd46-103">C# 3.0 ve sonraki durumlarda, otomatik olarak uygulanan özellikler, özellik erişimcilerinde ek bir mantık gerekmediğinde özellik bildirimini daha kısa yapar.</span><span class="sxs-lookup"><span data-stu-id="fdd46-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="fdd46-104">Ayrıca, istemci kodunun nesneler oluşturmasını da sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="fdd46-104">They also enable client code to create objects.</span></span> <span data-ttu-id="fdd46-105">Aşağıdaki örnekte gösterildiği gibi bir özelliği beyan ettiğinizde, derleyici yalnızca mülkün `get` ve `set` erişime sahip olanların aracılığıyla erişilebilen özel, anonim bir destek alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdd46-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="fdd46-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdd46-106">Example</span></span>

<span data-ttu-id="fdd46-107">Aşağıdaki örnek, bazı otomatik uygulanan özelliklere sahip basit bir sınıfı gösterir:</span><span class="sxs-lookup"><span data-stu-id="fdd46-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="fdd46-108">Arabirimlerde otomatik olarak uygulanan özellikleri bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd46-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="fdd46-109">Otomatik olarak uygulanan özellikler özel örnek destek alanı bildirir ve arabirimler örnek alanlarını beyan emeyebilir.</span><span class="sxs-lookup"><span data-stu-id="fdd46-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="fdd46-110">Bir gövde tanımlamadan bir arabirimde bir özelliği bildirmek, bu arabirimi uygulayan her tür tarafından uygulanması gereken erişimci bir özelliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="fdd46-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="fdd46-111">C# 6 ve sonraki durumlarda, otomatik olarak uygulanan özellikleri alanlara benzer şekilde başharfekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fdd46-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="fdd46-112">Önceki örnekte gösterilen sınıf mutable.</span><span class="sxs-lookup"><span data-stu-id="fdd46-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="fdd46-113">İstemci kodu oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="fdd46-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="fdd46-114">Önemli davranış (yöntem) yanı sıra veri içeren karmaşık sınıflarda, genellikle ortak özelliklere sahip olmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fdd46-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="fdd46-115">Ancak, yalnızca bir değer kümesini (veri) kapsülleyen ve çok az veya hiç davranışı olmayan küçük sınıflar veya yapılar için, ayarlanan erişimi [özel](../../language-reference/keywords/private.md) (tüketicilere değişmez) olarak beyan ederek veya yalnızca bir erişime sahip (oluşturucu hariç her yerde değişmez) beyan ederek nesneleri değişmez hale getirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd46-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="fdd46-116">Daha fazla bilgi için, [otomatik olarak uygulanan özelliklere sahip hafif bir sınıfın nasıl uygulanacağını](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)görün.</span><span class="sxs-lookup"><span data-stu-id="fdd46-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdd46-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdd46-117">See also</span></span>

- [<span data-ttu-id="fdd46-118">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fdd46-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="fdd46-119">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="fdd46-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
