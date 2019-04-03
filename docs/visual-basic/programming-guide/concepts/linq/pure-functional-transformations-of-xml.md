---
title: Saf işlevsel dönüşümlere XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
ms.openlocfilehash: 48149faba1c41583ab4e50c539d52e4caf90592a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843428"
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="86c23-102">Saf işlevsel dönüşümlere XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86c23-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="86c23-103">Bu bölüm için XML işlevsel dönüşümü öğretici sağlar.</span><span class="sxs-lookup"><span data-stu-id="86c23-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="86c23-104">Bu kavramlarla açıklamalarını içerir ve işlevsel dönüşümlere ve bir XML belgesi işlemek için işlevsel dönüşümlere kullanma örnekleri kullanmak için anlamanız gereken dil oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86c23-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="86c23-105">Bu öğreticide LINQ için XML kod örnekleri sağlasa da, tüm temel kavramları diğer LINQ teknolojileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="86c23-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="86c23-106">[Öğreticisi: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici, her eskisinin oluşturmayı örnekler, bir dizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="86c23-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="86c23-107">Bu örnekler, XML düzenleme saf işlevsel dönüşümsel yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="86c23-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="86c23-108">Bu öğreticide, Visual Basic bilgisine varsayılır.</span><span class="sxs-lookup"><span data-stu-id="86c23-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="86c23-109">Dil yapıları ayrıntılı semantikleri, bu öğreticide sağlanmaz, ancak uygun dil belgelerine bağlantılar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="86c23-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="86c23-110">Temel bilgisayar bilimi kavramları ve XML XML ad alanları da dahil olmak üzere, bilgisine da varsayılır.</span><span class="sxs-lookup"><span data-stu-id="86c23-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86c23-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="86c23-111">In This Section</span></span>  
  
|<span data-ttu-id="86c23-112">Konu</span><span class="sxs-lookup"><span data-stu-id="86c23-112">Topic</span></span>|<span data-ttu-id="86c23-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86c23-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="86c23-114">Saf işlevsel dönüşümlere (Visual Basic) giriş</span><span class="sxs-lookup"><span data-stu-id="86c23-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="86c23-115">İşlevsel dönüşümlere açıklanmakta ve ilgili terimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86c23-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="86c23-116">Öğretici: Ertelenmiş yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86c23-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)|<span data-ttu-id="86c23-117">Geç değerlendirme ve ertelenmiş yürütme ayrıntılı açıklar.</span><span class="sxs-lookup"><span data-stu-id="86c23-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="86c23-118">Öğretici: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme</span><span class="sxs-lookup"><span data-stu-id="86c23-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="86c23-119">İşlevsel dönüşüm gösteren öğretici.</span><span class="sxs-lookup"><span data-stu-id="86c23-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86c23-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c23-120">See also</span></span>

- [<span data-ttu-id="86c23-121">(Visual Basic) XML ağaçlarını sorgulama</span><span class="sxs-lookup"><span data-stu-id="86c23-121">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
