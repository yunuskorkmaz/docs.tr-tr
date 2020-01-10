---
title: Otomatik uygulanan özellikler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 76f16a66fbc01a6a69d91136cfbfe5805b91aea3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705645"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="17fb1-102">Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="17fb1-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="17fb1-103">C# 3,0 ve sonraki sürümlerde, özellik erişimcilerinde ek bir mantık gerekmediği zaman otomatik uygulanan özellikler özellik bildirimini daha kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="17fb1-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="17fb1-104">Ayrıca, istemci kodunun nesne oluşturmasını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="17fb1-104">They also enable client code to create objects.</span></span> <span data-ttu-id="17fb1-105">Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve `set` erişimcileri aracılığıyla erişilebilen özel, anonim bir destek alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17fb1-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17fb1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="17fb1-106">Example</span></span>  
 <span data-ttu-id="17fb1-107">Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="17fb1-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 <span data-ttu-id="17fb1-108">C# 6 ve sonrasında, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17fb1-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="17fb1-109">Önceki örnekte gösterilen sınıf değişebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="17fb1-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="17fb1-110">İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="17fb1-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="17fb1-111">Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="17fb1-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="17fb1-112">Bununla birlikte, yalnızca bir değer kümesini (veri) kapsülleyen ve hiç davranışlarına sahip olan küçük sınıflar veya yapılar için, küme erişimcisini [Private](../../language-reference/keywords/private.md) (Sabit-tüketiciler) olarak bildirerek veya yalnızca bir get erişimcisi bildirerek (Oluşturucu dışında sabit olarak) nesneleri sabit hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17fb1-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="17fb1-113">Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="17fb1-113">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="17fb1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17fb1-114">See also</span></span>

- [<span data-ttu-id="17fb1-115">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="17fb1-115">Properties</span></span>](./properties.md)
- [<span data-ttu-id="17fb1-116">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="17fb1-116">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
