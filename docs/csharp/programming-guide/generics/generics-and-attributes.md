---
title: Genel ler ve Öznitelikler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703032"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="ee1d3-102">Genel Türler ve Öznitelikler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ee1d3-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="ee1d3-103">Öznitelikler genel olmayan türler gibi genel türlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="ee1d3-104">Öznitelikleri uygulama hakkında daha fazla bilgi için, [Bkz. Öznitelikler.](../concepts/attributes/index.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d3-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="ee1d3-105">Özel özniteliklere yalnızca, tür bağımsız değişkenleri verilen genel türler olan açık genel türlere ve tüm tür parametreleri için bağımsız değişkensağlayan kapalı yapılı genel türlere başvurmaizni verilir.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="ee1d3-106">Aşağıdaki örneklerde bu özel özniteliği kullanın:</span><span class="sxs-lookup"><span data-stu-id="ee1d3-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="ee1d3-107">Bir öznitelik açık genel bir türbaşvuru olabilir:</span><span class="sxs-lookup"><span data-stu-id="ee1d3-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="ee1d3-108">Uygun sayıda virgül kullanarak birden çok tür parametresini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="ee1d3-109">Bu örnekte, `GenericClass2` iki tür parametre vardır:</span><span class="sxs-lookup"><span data-stu-id="ee1d3-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="ee1d3-110">Bir öznitelik kapalı oluşturulmuş genel türe başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="ee1d3-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="ee1d3-111">Genel bir tür parametresine başvuran bir öznitelik derleme zamanı hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="ee1d3-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="ee1d3-112">Genel bir tür <xref:System.Attribute>devralamaz:</span><span class="sxs-lookup"><span data-stu-id="ee1d3-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="ee1d3-113">Genel bir tür veya çalışma zamanında tür parametresi hakkında bilgi <xref:System.Reflection>edinmek için .</span><span class="sxs-lookup"><span data-stu-id="ee1d3-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="ee1d3-114">Daha fazla bilgi için [Genel Bilgiler ve Yansıma](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d3-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1d3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-115">See also</span></span>

- [<span data-ttu-id="ee1d3-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee1d3-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ee1d3-117">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ee1d3-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="ee1d3-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee1d3-118">Attributes</span></span>](../../../standard/attributes/index.md)
