---
title: Genel türler ve öznitelikler-C# Programlama Kılavuzu
description: Genel türlere öznitelikler uygulama hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 94378e44782169141314890bf90f050fdb6b5b79
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184215"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="31b7a-104">Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="31b7a-104">Generics and Attributes (C# Programming Guide)</span></span>

<span data-ttu-id="31b7a-105">Öznitelikler Genel türlere genel olmayan türlerle aynı şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="31b7a-105">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="31b7a-106">Öznitelikleri uygulama hakkında daha fazla bilgi için bkz. [öznitelikler](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="31b7a-106">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="31b7a-107">Özel özniteliklerin yalnızca tür bağımsız değişkenleri sağlanmayan genel türler ve tüm tür parametreleri için bağımsız değişkenler sağlayan kapalı oluşturulmuş genel türler olan açık Genel türlere başvurmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="31b7a-107">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="31b7a-108">Aşağıdaki örnekler bu özel özniteliği kullanır:</span><span class="sxs-lookup"><span data-stu-id="31b7a-108">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="31b7a-109">Bir öznitelik, açık bir genel türe başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="31b7a-109">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="31b7a-110">Uygun sayıda virgül kullanarak birden çok tür parametresi belirtin.</span><span class="sxs-lookup"><span data-stu-id="31b7a-110">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="31b7a-111">Bu örnekte, `GenericClass2` iki tür parametresi vardır:</span><span class="sxs-lookup"><span data-stu-id="31b7a-111">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="31b7a-112">Bir öznitelik, Kapalı oluşturulmuş genel bir türe başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="31b7a-112">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="31b7a-113">Genel tür parametresine başvuran bir öznitelik, derleme zamanı hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="31b7a-113">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="31b7a-114">Genel bir tür şuradan devralınabilir <xref:System.Attribute> :</span><span class="sxs-lookup"><span data-stu-id="31b7a-114">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="31b7a-115">Çalışma zamanında genel bir tür veya tür parametresi hakkında bilgi edinmek için, yöntemlerini kullanabilirsiniz <xref:System.Reflection> .</span><span class="sxs-lookup"><span data-stu-id="31b7a-115">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="31b7a-116">Daha fazla bilgi için bkz. [Genel türler ve yansıma](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="31b7a-116">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b7a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31b7a-117">See also</span></span>

- [<span data-ttu-id="31b7a-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="31b7a-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="31b7a-119">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="31b7a-119">Generics</span></span>](./index.md)
- [<span data-ttu-id="31b7a-120">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31b7a-120">Attributes</span></span>](../../../standard/attributes/index.md)
