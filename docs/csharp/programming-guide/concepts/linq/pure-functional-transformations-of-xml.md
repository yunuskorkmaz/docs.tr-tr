---
title: Saf işlevsel dönüşümleri XML (C#)
ms.date: 07/20/2015
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
ms.openlocfilehash: 7bbe5735541432108794959a7889976d4951fffd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336716"
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="42c8c-102">Saf işlevsel dönüşümleri XML (C#)</span><span class="sxs-lookup"><span data-stu-id="42c8c-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="42c8c-103">Bu bölümde bir işlev dönüştürme öğretici için XML sağlar.</span><span class="sxs-lookup"><span data-stu-id="42c8c-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="42c8c-104">Bu kavramlarla açıklamalarını içerir ve dil yapıları işlevsel dönüşümler ve bir XML belgesi işlemek için işlevsel dönüştürmeleri kullanma örnekleri kullanmak için anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="42c8c-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="42c8c-105">Bu öğretici LINQ için XML kod örnekleri sağlasa da, tüm temel kavramlarını diğer LINQ teknolojileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="42c8c-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="42c8c-106">[Öğreticisi: WordprocessingML belgede (C#) içerik düzenleme](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) Eğitmeni her önceki bir derleme örnekler, bir dizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="42c8c-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="42c8c-107">Bu örnekler, XML düzenleme saf işlevsel transformational yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="42c8c-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="42c8c-108">Bu öğretici bilgisine sahip C# varsayar.</span><span class="sxs-lookup"><span data-stu-id="42c8c-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="42c8c-109">Bu öğreticide dil yapıları ayrıntılı semantiği sağlanmayan, ancak uygun dil belgelere bağlantılar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42c8c-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="42c8c-110">Temel bilgisayar bilimi kavramları ve XML ad alanları dahil olmak üzere XML bilgili olduğu da varsayılır.</span><span class="sxs-lookup"><span data-stu-id="42c8c-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42c8c-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="42c8c-111">In This Section</span></span>  
  
|<span data-ttu-id="42c8c-112">Konu</span><span class="sxs-lookup"><span data-stu-id="42c8c-112">Topic</span></span>|<span data-ttu-id="42c8c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42c8c-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="42c8c-114">Giriş saf işlevsel Dönüşümleri (C#)</span><span class="sxs-lookup"><span data-stu-id="42c8c-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="42c8c-115">İşlev dönüşümleri açıklar ve ilgili terimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="42c8c-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="42c8c-116">Öğretici: Sorguları birlikte (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="42c8c-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="42c8c-117">Geç değerlendirme ve ayrıntılı ertelenmiş yürütme açıklar.</span><span class="sxs-lookup"><span data-stu-id="42c8c-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="42c8c-118">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)</span><span class="sxs-lookup"><span data-stu-id="42c8c-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="42c8c-119">İşlev dönüştürme gösteren bir öğretici.</span><span class="sxs-lookup"><span data-stu-id="42c8c-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42c8c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42c8c-120">See Also</span></span>  
 [<span data-ttu-id="42c8c-121">Sorgulama XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="42c8c-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
