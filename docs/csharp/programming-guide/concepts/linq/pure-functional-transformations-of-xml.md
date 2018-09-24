---
title: Saf işlevsel dönüşümlere XML (C#)
ms.date: 07/20/2015
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
ms.openlocfilehash: e05c6167973b2342aafd51aad7d9102db9e94ae0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705416"
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="96bd0-102">Saf işlevsel dönüşümlere XML (C#)</span><span class="sxs-lookup"><span data-stu-id="96bd0-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="96bd0-103">Bu bölüm için XML işlevsel dönüşümü öğretici sağlar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="96bd0-104">Bu kavramlarla açıklamalarını içerir ve işlevsel dönüşümlere ve bir XML belgesi işlemek için işlevsel dönüşümlere kullanma örnekleri kullanmak için anlamanız gereken dil oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96bd0-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="96bd0-105">Bu öğreticide LINQ için XML kod örnekleri sağlasa da, tüm temel kavramları diğer LINQ teknolojileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="96bd0-106">[Öğretici: WordprocessingML belgesindeki (C#) içerik düzenleme](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici, her eskisinin oluşturmayı örnekler, bir dizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="96bd0-107">Bu örnekler, XML düzenleme saf işlevsel dönüşümsel yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="96bd0-108">Bu öğretici, C# bilgisine varsayar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="96bd0-109">Dil yapıları ayrıntılı semantikleri, bu öğreticide sağlanmaz, ancak uygun dil belgelerine bağlantılar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="96bd0-110">Temel bilgisayar bilimi kavramları ve XML XML ad alanları da dahil olmak üzere, bilgisine da varsayılır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96bd0-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="96bd0-111">In This Section</span></span>  
  
|<span data-ttu-id="96bd0-112">Konu</span><span class="sxs-lookup"><span data-stu-id="96bd0-112">Topic</span></span>|<span data-ttu-id="96bd0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96bd0-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="96bd0-114">Giriş saf işlevsel dönüşümlere (C#)</span><span class="sxs-lookup"><span data-stu-id="96bd0-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="96bd0-115">İşlevsel dönüşümlere açıklanmakta ve ilgili terimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="96bd0-116">Öğretici: Sorguları birbirine (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="96bd0-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="96bd0-117">Geç değerlendirme ve ertelenmiş yürütme ayrıntılı açıklar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="96bd0-118">Öğretici: WordprocessingML belgesindeki (C#) içerik düzenleme</span><span class="sxs-lookup"><span data-stu-id="96bd0-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="96bd0-119">İşlevsel dönüşüm gösteren öğretici.</span><span class="sxs-lookup"><span data-stu-id="96bd0-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96bd0-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-120">See Also</span></span>

- [<span data-ttu-id="96bd0-121">XML ağaçlarını sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="96bd0-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
