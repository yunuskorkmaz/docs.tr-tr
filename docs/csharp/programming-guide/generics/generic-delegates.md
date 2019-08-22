---
title: Genel Temsilciler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 31ab511bf88bfbc2134029564ecbf70aa75119d7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659843"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="60ea3-102">Genel Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="60ea3-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="60ea3-103">Bir [temsilci](../../language-reference/keywords/delegate.md) kendi tür parametrelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="60ea3-103">A [delegate](../../language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="60ea3-104">Genel temsilciye başvuran kod, aşağıdaki örnekte gösterildiği gibi, bir genel sınıf örneği oluşturulurken veya genel bir yöntemi çağırırken olduğu gibi kapalı bir oluşturulmuş tür oluşturmak için tür bağımsız değişkenini belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="60ea3-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="60ea3-105">C#sürüm 2,0 ' de, somut ve genel temsilci türleri için geçerli olan Yöntem grubu dönüştürmesi adlı yeni bir özellik vardır ve bu Basitleştirilmiş söz dizimi ile önceki satırı yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="60ea3-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="60ea3-106">Genel bir sınıf içinde tanımlanan temsilciler, sınıf yöntemlerinin olduğu şekilde genel sınıf türü parametrelerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="60ea3-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="60ea3-107">Temsilciye başvuran kodun, kapsayan sınıfın tür bağımsız değişkenini aşağıdaki gibi belirtmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="60ea3-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="60ea3-108">Genel Temsilciler, genellikle gönderen bağımsız değişkeni kesin olarak türlenebilir ve artık ve öğesinden <xref:System.Object>bir tür olmak zorunda kalabileceğinden, tipik tasarım düzenine göre olayları tanımlamaya yarar.</span><span class="sxs-lookup"><span data-stu-id="60ea3-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="60ea3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60ea3-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="60ea3-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="60ea3-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="60ea3-111">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="60ea3-111">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="60ea3-112">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="60ea3-112">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="60ea3-113">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="60ea3-113">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="60ea3-114">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="60ea3-114">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="60ea3-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="60ea3-115">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="60ea3-116">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="60ea3-116">Generics</span></span>](../../../standard/generics/index.md)
