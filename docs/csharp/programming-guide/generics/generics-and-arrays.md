---
title: Genel türler ve diziler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f5b82d470f728129fc76851bc2708e20085d5326
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589681"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="b54c5-102">Genel Türler ve Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b54c5-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="b54c5-103">2,0 C# ve üzeri sürümlerde, sıfır alt sınırı olan tek boyutlu diziler otomatik olarak uygulanır <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="b54c5-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="b54c5-104">Bu, diziler ve diğer koleksiyon türleri arasında yinelemek için aynı kodu kullanan genel yöntemler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b54c5-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="b54c5-105">Bu teknik öncelikle koleksiyonlardaki verileri okumak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b54c5-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="b54c5-106"><xref:System.Collections.Generic.IList%601> Arabirim bir diziye öğe eklemek veya kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b54c5-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="b54c5-107">Bu bağlamdaki bir dizide gibi <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bir yöntemi çağırmaya çalışırsanız bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b54c5-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="b54c5-108">Aşağıdaki kod örneği, bir <xref:System.Collections.Generic.IList%601> giriş parametresi alan tek bir genel yöntemin, bu durumda bir tamsayılar dizisi olan bir liste ve dizi boyunca nasıl yineleyebileceğinizi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b54c5-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="b54c5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b54c5-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b54c5-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b54c5-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b54c5-111">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b54c5-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="b54c5-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="b54c5-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="b54c5-113">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b54c5-113">Generics</span></span>](~/docs/standard/generics/index.md)
