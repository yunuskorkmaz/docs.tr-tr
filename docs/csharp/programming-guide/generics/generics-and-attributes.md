---
title: Genel türler ve öznitelikler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 000ce5a72cede9d1f23b0efb7ccf8638090a9032
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979599"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="e9a9d-102">Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e9a9d-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="e9a9d-103">Genel türler için öznitelikleri genel olmayan türleri aynı şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e9a9d-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="e9a9d-104">Öznitelikleri uygulama ile ilgili daha fazla bilgi için bkz: [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9a9d-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="e9a9d-105">Özel öznitelikler için hiçbir tür bağımsız değişkenleri sağlanan genel türler ve tüm tür parametreleri için bağımsız değişkenleri kapalı oluşturulan genel türler, açık genel türler başvurmak için yalnızca izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e9a9d-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="e9a9d-106">Aşağıdaki örnekler, bu özel öznitelik kullanın:</span><span class="sxs-lookup"><span data-stu-id="e9a9d-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="e9a9d-107">Öznitelik, bir açık genel tür başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9a9d-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="e9a9d-108">Uygun sayıda virgül kullanarak birden çok tür parametreleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="e9a9d-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="e9a9d-109">Bu örnekte, `GenericClass2` iki tür parametreleri vardır:</span><span class="sxs-lookup"><span data-stu-id="e9a9d-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="e9a9d-110">Öznitelik, kapalı bir oluşturulmuş genel tür başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9a9d-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="e9a9d-111">Genel tür parametresine başvuran bir öznitelik, bir derleme zamanı hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="e9a9d-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="e9a9d-112">Genel tür devralamaz <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="e9a9d-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="e9a9d-113">Çalışma zamanında bir genel tür veya tür parametresi ile ilgili bilgi edinme yöntemlerini kullanabilirsiniz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="e9a9d-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="e9a9d-114">Daha fazla bilgi için [genel türler ve yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="e9a9d-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a9d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9a9d-115">See also</span></span>

- [<span data-ttu-id="e9a9d-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e9a9d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e9a9d-117">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e9a9d-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="e9a9d-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9a9d-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
