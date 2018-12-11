---
title: Genel türler ve öznitelikler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 35244ce33902760c2a0d3d8bda3181097f7ca38e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245187"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="08bc9-102">Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="08bc9-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="08bc9-103">Genel türler için öznitelikleri genel olmayan türleri aynı şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="08bc9-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="08bc9-104">Öznitelikleri uygulama ile ilgili daha fazla bilgi için bkz: [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="08bc9-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="08bc9-105">Özel öznitelikler için hiçbir tür bağımsız değişkenleri sağlanan genel türler ve tüm tür parametreleri için bağımsız değişkenleri kapalı oluşturulan genel türler, açık genel türler başvurmak için yalnızca izin verilir.</span><span class="sxs-lookup"><span data-stu-id="08bc9-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="08bc9-106">Aşağıdaki örnekler, bu özel öznitelik kullanın:</span><span class="sxs-lookup"><span data-stu-id="08bc9-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="08bc9-107">Öznitelik, bir açık genel tür başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="08bc9-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="08bc9-108">Uygun sayıda virgül kullanarak birden çok tür parametreleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="08bc9-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="08bc9-109">Bu örnekte, `GenericClass2` iki tür parametreleri vardır:</span><span class="sxs-lookup"><span data-stu-id="08bc9-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="08bc9-110">Öznitelik, kapalı bir oluşturulmuş genel tür başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="08bc9-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="08bc9-111">Genel tür parametresine başvuran bir öznitelik, bir derleme zamanı hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="08bc9-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="08bc9-112">Genel tür devralamaz <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="08bc9-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="08bc9-113">Çalışma zamanında bir genel tür veya tür parametresi ile ilgili bilgi edinme yöntemlerini kullanabilirsiniz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="08bc9-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="08bc9-114">Daha fazla bilgi için [genel türler ve yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="08bc9-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08bc9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08bc9-115">See Also</span></span>

- [<span data-ttu-id="08bc9-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="08bc9-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="08bc9-117">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="08bc9-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
- [<span data-ttu-id="08bc9-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08bc9-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
