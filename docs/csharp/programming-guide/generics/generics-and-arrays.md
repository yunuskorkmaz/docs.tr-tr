---
title: Genel türler ve diziler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703019"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="04c62-102">Genel Türler ve Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="04c62-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="04c62-103">C# 2,0 ve üzeri sürümlerde, sıfır alt sınırı olan tek boyutlu diziler otomatik olarak <xref:System.Collections.Generic.IList%601>uygular.</span><span class="sxs-lookup"><span data-stu-id="04c62-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="04c62-104">Bu, diziler ve diğer koleksiyon türleri arasında yinelemek için aynı kodu kullanan genel yöntemler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="04c62-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="04c62-105">Bu teknik öncelikle koleksiyonlardaki verileri okumak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="04c62-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="04c62-106"><xref:System.Collections.Generic.IList%601> arabirimi bir diziye öğe eklemek veya kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="04c62-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="04c62-107">Bu bağlamdaki bir dizide <xref:System.Collections.Generic.IList%601.RemoveAt%2A> gibi bir <xref:System.Collections.Generic.IList%601> yöntemi çağırmayı denerseniz bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="04c62-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="04c62-108">Aşağıdaki kod örneği, bir <xref:System.Collections.Generic.IList%601> giriş parametresi alan tek bir genel yöntemin, bu durumda bir tamsayılar dizisi olan bir liste ve dizi boyunca nasıl yineleyebileceğinizi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="04c62-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="04c62-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04c62-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="04c62-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="04c62-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04c62-111">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="04c62-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="04c62-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="04c62-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="04c62-113">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="04c62-113">Generics</span></span>](../../../standard/generics/index.md)
