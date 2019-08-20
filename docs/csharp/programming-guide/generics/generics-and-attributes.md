---
title: Genel türler ve öznitelikler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 99a24a7069145dfad5ce6c9c91f2a8653eb9a224
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589632"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="8cab6-102">Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8cab6-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="8cab6-103">Öznitelikler Genel türlere genel olmayan türlerle aynı şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8cab6-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="8cab6-104">Öznitelikleri uygulama hakkında daha fazla bilgi için bkz. [öznitelikler](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="8cab6-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="8cab6-105">Özel özniteliklerin yalnızca tür bağımsız değişkenleri sağlanmayan genel türler ve tüm tür parametreleri için bağımsız değişkenler sağlayan kapalı oluşturulmuş genel türler olan açık Genel türlere başvurmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="8cab6-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="8cab6-106">Aşağıdaki örnekler bu özel özniteliği kullanır:</span><span class="sxs-lookup"><span data-stu-id="8cab6-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="8cab6-107">Bir öznitelik, açık bir genel türe başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="8cab6-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="8cab6-108">Uygun sayıda virgül kullanarak birden çok tür parametresi belirtin.</span><span class="sxs-lookup"><span data-stu-id="8cab6-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="8cab6-109">Bu örnekte, `GenericClass2` iki tür parametresi vardır:</span><span class="sxs-lookup"><span data-stu-id="8cab6-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="8cab6-110">Bir öznitelik, Kapalı oluşturulmuş genel bir türe başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="8cab6-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="8cab6-111">Genel tür parametresine başvuran bir öznitelik, derleme zamanı hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="8cab6-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="8cab6-112">Genel bir tür şuradan <xref:System.Attribute>devralınabilir:</span><span class="sxs-lookup"><span data-stu-id="8cab6-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="8cab6-113">Çalışma zamanında genel bir tür veya tür parametresi hakkında bilgi edinmek için, yöntemlerini <xref:System.Reflection>kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cab6-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="8cab6-114">Daha fazla bilgi için bkz. [Genel türler ve yansıma](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="8cab6-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cab6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cab6-115">See also</span></span>

- [<span data-ttu-id="8cab6-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8cab6-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8cab6-117">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="8cab6-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="8cab6-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8cab6-118">Attributes</span></span>](../../../standard/attributes/index.md)
