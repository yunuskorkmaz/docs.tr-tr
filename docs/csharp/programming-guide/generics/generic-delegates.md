---
title: Genel Temsilciler-C# Programlama Kılavuzu
description: C# dilinde Genel Temsilciler kullanma hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: d99271ca9f12e95743d633caac16aaa4151e9c41
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301911"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="5d393-104">Genel Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5d393-104">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="5d393-105">Bir [temsilci](../../language-reference/builtin-types/reference-types.md) kendi tür parametrelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5d393-105">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="5d393-106">Genel temsilciye başvuran kod, aşağıdaki örnekte gösterildiği gibi, bir genel sınıf örneği oluşturulurken veya genel bir yöntemi çağırırken olduğu gibi kapalı bir oluşturulmuş tür oluşturmak için tür bağımsız değişkenini belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="5d393-106">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="5d393-107">C# sürüm 2,0, somut ve genel temsilci türleri için geçerli olan ve bu Basitleştirilmiş söz dizimi ile önceki satırı yazmanızı sağlayan yöntem grubu dönüştürmesi adlı yeni bir özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5d393-107">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="5d393-108">Genel bir sınıf içinde tanımlanan temsilciler, sınıf yöntemlerinin olduğu şekilde genel sınıf türü parametrelerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5d393-108">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="5d393-109">Temsilciye başvuran kodun, kapsayan sınıfın tür bağımsız değişkenini aşağıdaki gibi belirtmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="5d393-109">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="5d393-110">Genel Temsilciler, genellikle gönderen bağımsız değişkeni kesin olarak türlenebilir ve artık ve öğesinden bir tür olmak zorunda kalabileceğinden, tipik tasarım düzenine göre olayları tanımlamaya yarar <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="5d393-110">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="5d393-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d393-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="5d393-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5d393-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5d393-113">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="5d393-113">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="5d393-114">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5d393-114">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="5d393-115">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="5d393-115">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="5d393-116">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="5d393-116">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="5d393-117">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5d393-117">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="5d393-118">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5d393-118">Generics</span></span>](../../../standard/generics/index.md)
