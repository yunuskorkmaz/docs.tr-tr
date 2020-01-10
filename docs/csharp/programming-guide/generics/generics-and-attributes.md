---
title: Genel türler ve öznitelikler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703032"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="b3c9d-102">Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b3c9d-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="b3c9d-103">Öznitelikler Genel türlere genel olmayan türlerle aynı şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b3c9d-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="b3c9d-104">Öznitelikleri uygulama hakkında daha fazla bilgi için bkz. [öznitelikler](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3c9d-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="b3c9d-105">Özel özniteliklerin yalnızca tür bağımsız değişkenleri sağlanmayan genel türler ve tüm tür parametreleri için bağımsız değişkenler sağlayan kapalı oluşturulmuş genel türler olan açık Genel türlere başvurmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="b3c9d-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="b3c9d-106">Aşağıdaki örnekler bu özel özniteliği kullanır:</span><span class="sxs-lookup"><span data-stu-id="b3c9d-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="b3c9d-107">Bir öznitelik, açık bir genel türe başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="b3c9d-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="b3c9d-108">Uygun sayıda virgül kullanarak birden çok tür parametresi belirtin.</span><span class="sxs-lookup"><span data-stu-id="b3c9d-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="b3c9d-109">Bu örnekte `GenericClass2` iki tür parametreye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b3c9d-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="b3c9d-110">Bir öznitelik, Kapalı oluşturulmuş genel bir türe başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="b3c9d-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="b3c9d-111">Genel tür parametresine başvuran bir öznitelik, derleme zamanı hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="b3c9d-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="b3c9d-112">Genel bir tür <xref:System.Attribute>devralınabilir:</span><span class="sxs-lookup"><span data-stu-id="b3c9d-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="b3c9d-113">Çalışma zamanında genel bir tür veya tür parametresi hakkında bilgi almak için <xref:System.Reflection>yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3c9d-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="b3c9d-114">Daha fazla bilgi için bkz. [Genel türler ve yansıma](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="b3c9d-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c9d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3c9d-115">See also</span></span>

- [<span data-ttu-id="b3c9d-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b3c9d-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b3c9d-117">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b3c9d-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="b3c9d-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3c9d-118">Attributes</span></span>](../../../standard/attributes/index.md)
