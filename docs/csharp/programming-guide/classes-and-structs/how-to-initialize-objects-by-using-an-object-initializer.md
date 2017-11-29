---
title: "Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesneleri Başlatma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1e65f8519062f6bceeb466a3b72c5719c0918f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="c7a8d-102">Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesneleri Başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c7a8d-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="c7a8d-103">Nesne başlatıcıları türde nesne türü için bir oluşturucu açıkça çağırmadan bildirim temelli bir şekilde başlatmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="c7a8d-104">Aşağıdaki örnekler nesne başlatıcıları adlandırılmış nesnelerinin ile nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="c7a8d-105">Derleyici işlemleri başlatıcıları ilk varsayılan örnek oluşturucusu erişme ve üye başlatmaları işleme nesne.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="c7a8d-106">Bu nedenle, varsayılan oluşturucu olarak bildirilirse `private` sınıfında genel erişim gerektiren nesne başlatıcıları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="c7a8d-107">Anonim bir tür tanımlanıyorsa nesne Başlatıcı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="c7a8d-108">Daha fazla bilgi için bkz: [nasıl yapılır: dönüş alt öğesi özelliklerin sorguda](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="c7a8d-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7a8d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7a8d-109">Example</span></span>  
 <span data-ttu-id="c7a8d-110">Aşağıdaki örnek yeni bir başlatma gösterilmektedir `StudentName` nesne başlatıcıları kullanarak türü.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c7a8d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7a8d-111">Example</span></span>  
 <span data-ttu-id="c7a8d-112">Aşağıdaki örnek, bir koleksiyonu başlatmak gösterilmiştir `StudentName` koleksiyon Başlatıcısı kullanarak türleri.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="c7a8d-113">Koleksiyon başlatıcısı bir dizi virgülle ayrılmış nesne başlatıcıları olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7a8d-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c7a8d-114">Compiling the Code</span></span>  
 <span data-ttu-id="c7a8d-115">Bu kodu çalıştırmak için kopyalayıp sınıfı içinde oluşturduğunuz bir Visual C# konsol uygulaması projesi yapıştırın [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7a8d-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a8d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7a8d-116">See Also</span></span>  
 [<span data-ttu-id="c7a8d-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7a8d-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c7a8d-118">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="c7a8d-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
