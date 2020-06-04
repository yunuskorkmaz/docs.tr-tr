---
title: Saf İşlevsel XML Dönüşümleri
ms.date: 07/20/2015
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
ms.openlocfilehash: 60ec6a5f9c643ea5cc0511f48356d6bfa3ad5748
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396330"
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="3c04d-102">XML 'nin saf Işlevsel dönüştürmeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c04d-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="3c04d-103">Bu bölüm, XML için işlevsel bir dönüşüm öğreticisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c04d-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="3c04d-104">Bu, işlevsel dönüştürmeleri kullanmak için anlamanız gereken ana kavramların ve dil yapılarının açıklamalarını ve bir XML belgesini işlemek için işlevsel dönüşümler kullanma örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3c04d-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="3c04d-105">Bu öğretici LINQ to XML kod örnekleri sunmakla birlikte, temel kavramların hepsi diğer LINQ teknolojileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3c04d-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="3c04d-106">[Öğretici: bir WordprocessingML belgesi (Visual Basic) öğreticisindeki Içerik işleme](tutorial-manipulating-content-in-a-wordprocessingml-document.md) , her biri bir öncekini oluşturmak için bir dizi örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c04d-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="3c04d-107">Bu örnekler, XML 'nin işlenmesine yönelik saf işlevsel dönüşüm yaklaşımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c04d-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="3c04d-108">Bu öğreticide Visual Basic çalışan bir bilgi varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c04d-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="3c04d-109">Dil yapılarının ayrıntılı semantiği Bu öğreticide sağlanmaz, ancak uygun şekilde dil belgelerine bağlantılar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3c04d-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="3c04d-110">XML ad alanları da dahil olmak üzere temel bilgisayar bilimi kavramları ve XML 'nin çalışma bilgisi de kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3c04d-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c04d-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3c04d-111">In This Section</span></span>  
  
|<span data-ttu-id="3c04d-112">Konu başlığı</span><span class="sxs-lookup"><span data-stu-id="3c04d-112">Topic</span></span>|<span data-ttu-id="3c04d-113">Description</span><span class="sxs-lookup"><span data-stu-id="3c04d-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3c04d-114">Saf Işlevsel dönüşümlere giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c04d-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)|<span data-ttu-id="3c04d-115">İşlevsel dönüştürmeleri açıklar ve ilgili terminolojiyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c04d-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="3c04d-116">Öğretici: ertelenmiş yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c04d-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)|<span data-ttu-id="3c04d-117">Geç değerlendirmeyi ve ertelenmiş yürütmeyi ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="3c04d-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="3c04d-118">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c04d-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="3c04d-119">İşlevsel bir dönüştürmeyi gösteren bir öğretici.</span><span class="sxs-lookup"><span data-stu-id="3c04d-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c04d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c04d-120">See also</span></span>

- [<span data-ttu-id="3c04d-121">XML ağaçlarını sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c04d-121">Querying XML Trees (Visual Basic)</span></span>](querying-xml-trees.md)
