---
title: Jenerik ler ve Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703019"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="d8ea7-102">Genel Türler ve Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d8ea7-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="d8ea7-103">C# 2.0 ve sonraki durumlarda, sıfır ın alt sınırı olan <xref:System.Collections.Generic.IList%601>tek boyutlu diziler otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="d8ea7-104">Bu, diziler ve diğer koleksiyon türleri arasında aynı kodu yinelemek için kullanabileceğiniz genel yöntemler oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="d8ea7-105">Bu teknik öncelikle koleksiyonlarda veri okumak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="d8ea7-106">Arabirim, <xref:System.Collections.Generic.IList%601> bir diziden öğe eklemek veya kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="d8ea7-107">Bu bağlamda bir dizi gibi <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bir yöntem çağırmaya çalışırsanız bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="d8ea7-108">Aşağıdaki kod örneği, giriş parametresi alan <xref:System.Collections.Generic.IList%601> tek bir genel yöntemin, bu durumda bir tamsayı dizisi olan bir liste ve dizi aracılığıyla nasıl yinelebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="d8ea7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="d8ea7-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d8ea7-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d8ea7-111">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d8ea7-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="d8ea7-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="d8ea7-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="d8ea7-113">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d8ea7-113">Generics</span></span>](../../../standard/generics/index.md)
