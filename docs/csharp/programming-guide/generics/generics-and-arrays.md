---
title: Genel türler ve diziler-C# Programlama Kılavuzu
description: C# programlamada genel türler ve Diziler hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f3d9e9e0c84d954278780e7598545f80aea0e58c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299051"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="c72d9-104">Genel Türler ve Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c72d9-104">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="c72d9-105">C# 2,0 ve üzeri sürümlerde, sıfır alt sınırı olan tek boyutlu diziler otomatik olarak uygulanır <xref:System.Collections.Generic.IList%601> .</span><span class="sxs-lookup"><span data-stu-id="c72d9-105">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="c72d9-106">Bu, diziler ve diğer koleksiyon türleri arasında yinelemek için aynı kodu kullanan genel yöntemler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c72d9-106">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="c72d9-107">Bu teknik öncelikle koleksiyonlardaki verileri okumak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c72d9-107">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="c72d9-108"><xref:System.Collections.Generic.IList%601>Arabirim bir diziye öğe eklemek veya kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c72d9-108">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="c72d9-109"><xref:System.Collections.Generic.IList%601>Bu bağlamdaki bir dizide gibi bir yöntemi çağırmaya çalışırsanız bir özel durum oluşturulur <xref:System.Collections.Generic.IList%601.RemoveAt%2A> .</span><span class="sxs-lookup"><span data-stu-id="c72d9-109">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="c72d9-110">Aşağıdaki kod örneği, bir giriş parametresi alan tek bir genel yöntemin <xref:System.Collections.Generic.IList%601> , bu durumda bir tamsayılar dizisi olan bir liste ve dizi boyunca nasıl yineleyebileceğinizi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c72d9-110">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="c72d9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c72d9-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="c72d9-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c72d9-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c72d9-113">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="c72d9-113">Generics</span></span>](./index.md)
- [<span data-ttu-id="c72d9-114">Diziler</span><span class="sxs-lookup"><span data-stu-id="c72d9-114">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="c72d9-115">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="c72d9-115">Generics</span></span>](../../../standard/generics/index.md)
