---
title: "Genel Türler ve Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94b144075fac44ff749474a5bfa8e81aaadc0a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="5d383-102">Genel Türler ve Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5d383-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="5d383-103">C# 2.0 ve daha sonra otomatik olarak sıfır alt sınır olan tek boyutlu diziler uygulamak <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="5d383-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="5d383-104">Bu, aynı kod diziler ve diğer koleksiyon türleri yinelemek için kullanabileceğiniz genel yöntemler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d383-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="5d383-105">Koleksiyonlarda verileri okumak için öncelikle bu teknik yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5d383-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="5d383-106"><xref:System.Collections.Generic.IList%601> Arabirimi eklemek veya dizisinden öğeleri kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5d383-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="5d383-107">Çağrı çalışırsanız, bir özel durum bir <xref:System.Collections.Generic.IList%601> yöntemi gibi <xref:System.Collections.Generic.IList%601.RemoveAt%2A> bu bağlamda bir dizi.</span><span class="sxs-lookup"><span data-stu-id="5d383-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="5d383-108">Aşağıdaki kod örneğinde alan tek bir genel yöntem nasıl gösterilmektedir bir <xref:System.Collections.Generic.IList%601> giriş parametresi bir listesi ve bir dizi yineleyebilirsiniz bu dizisi durumda.</span><span class="sxs-lookup"><span data-stu-id="5d383-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5d383-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d383-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="5d383-110">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5d383-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d383-111">Genel türler</span><span class="sxs-lookup"><span data-stu-id="5d383-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="5d383-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="5d383-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="5d383-113">Genel türler</span><span class="sxs-lookup"><span data-stu-id="5d383-113">Generics</span></span>](~/docs/standard/generics/index.md)
