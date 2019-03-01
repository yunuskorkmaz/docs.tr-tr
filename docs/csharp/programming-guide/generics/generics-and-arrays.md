---
title: Genel türler ve diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 145203d259b943bea1f43a9e49db2c7889bf914a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978922"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="53c35-102">Genel Türler ve Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="53c35-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="53c35-103">C# 2.0 ve sonraki sürümlerinde, otomatik olarak bir alt sınırı sıfır olan tek boyutlu diziler uygulamak <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="53c35-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="53c35-104">Bu, aynı kodu, diziler ve diğer koleksiyon türlerine yineleme yapmak için kullanabileceğiniz genel yöntemler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="53c35-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="53c35-105">Bu teknik koleksiyonlarda verileri okumak için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="53c35-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="53c35-106"><xref:System.Collections.Generic.IList%601> Arabirimi eklemek veya bir diziden öğeleri kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="53c35-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="53c35-107">Çağrılacak denerseniz bir özel durum bir <xref:System.Collections.Generic.IList%601> yöntemi gibi <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bu bağlamda bir dizi.</span><span class="sxs-lookup"><span data-stu-id="53c35-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="53c35-108">Aşağıdaki kod örneği, alan tek bir genel yöntem nasıl gösterir bir <xref:System.Collections.Generic.IList%601> giriş parametresi bir listesi ve bir dizi yinelenir bu tamsayı dizisi durumda.</span><span class="sxs-lookup"><span data-stu-id="53c35-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="53c35-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53c35-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="53c35-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="53c35-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="53c35-111">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="53c35-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="53c35-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="53c35-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="53c35-113">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="53c35-113">Generics</span></span>](~/docs/standard/generics/index.md)
