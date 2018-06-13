---
title: Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 3bfb4028fb5efce693abd83b40636b0149962e3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339689"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="9649a-102">Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9649a-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="9649a-103">Öznitelikler genel türleri için genel olmayan türleri aynı şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="9649a-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="9649a-104">Öznitelikleri uygulama ile ilgili daha fazla bilgi için bkz: [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="9649a-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="9649a-105">Özel öznitelikler yalnızca hiçbir tür bağımsız değişkenleri sağlanan genel türler ve tüm tür parametreleri için bağımsız değişkenleri eklemek kapalı oluşturulan genel türleri, açık genel türler başvurmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9649a-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="9649a-106">Aşağıdaki örnekler, bu özel öznitelik kullanın:</span><span class="sxs-lookup"><span data-stu-id="9649a-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="9649a-107">Açık genel tür bir öznitelik başvurusu yapabilir:</span><span class="sxs-lookup"><span data-stu-id="9649a-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="9649a-108">Uygun sayıda virgül kullanarak birden çok tür parametreleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="9649a-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="9649a-109">Bu örnekte, `GenericClass2` iki tür parametreye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9649a-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="9649a-110">Bir öznitelik kapalı oluşturulan genel bir tür başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="9649a-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="9649a-111">Genel tür parametresi başvuruda bulunan bir öznitelik, bir derleme zamanı hatası neden olur:</span><span class="sxs-lookup"><span data-stu-id="9649a-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="9649a-112">Genel bir tür devralınmalıdır olamaz <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="9649a-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="9649a-113">Çalışma zamanında bir genel tür veya tür parametresi hakkında bilgi almak için yöntemleri kullanabilirsiniz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="9649a-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="9649a-114">Daha fazla bilgi için bkz: [genel türler ve yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="9649a-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9649a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9649a-115">See Also</span></span>  
 [<span data-ttu-id="9649a-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9649a-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9649a-117">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="9649a-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="9649a-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9649a-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
