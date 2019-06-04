---
title: İşlevsel ve Yordam programlama karşılaştırması (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 1f713e54cefed5b1fcf8c29cd88aa7587a737327
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486952"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="bf468-102">İşlevsel ve Yordam programlama karşılaştırması (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bf468-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="bf468-103">XML uygulama çeşitli türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bf468-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="bf468-104">Bazı uygulamalar kaynak XML belgelerini alın ve kaynak belgeleri değerinden farklı bir şekil olan yeni XML belgeleri oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="bf468-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="bf468-105">Bazı uygulamalar kaynak XML belgelerini alın ve sonuç belgeleri, HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde üretmek.</span><span class="sxs-lookup"><span data-stu-id="bf468-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="bf468-106">Bazı uygulamalar kaynak XML belgelerini alın ve kayıtları bir veritabanına Ekle.</span><span class="sxs-lookup"><span data-stu-id="bf468-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="bf468-107">Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri almak ve XML belgeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf468-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="bf468-108">Bu XML uygulama türleri tümünün değildir, ancak bir temsilci uygulamak için bir XML Programcı olan işlevselliği türleri kümesini şunlardır.</span><span class="sxs-lookup"><span data-stu-id="bf468-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="bf468-109">Tüm bu tür uygulamalar, bir geliştirici alabilir ve karşıt iki yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="bf468-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="bf468-110">Bildirim temelli bir yaklaşım kullanarak işlevsel oluşturma.</span><span class="sxs-lookup"><span data-stu-id="bf468-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="bf468-111">Yordam kodu kullanarak bellek içi XML ağacı değişikliği.</span><span class="sxs-lookup"><span data-stu-id="bf468-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="bf468-112">LINQ to XML her iki yaklaşım destekler.</span><span class="sxs-lookup"><span data-stu-id="bf468-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="bf468-113">İşlevsel yaklaşım kullanırken, kaynak belgelerini alın ve istediğiniz şekli ile tamamen yeni sonucu belgeleri oluşturmak dönüşümleri yazın.</span><span class="sxs-lookup"><span data-stu-id="bf468-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="bf468-114">Bir XML ağacı yerinde değiştirirken, ekleme, silme ve düğümleri gerektiği şekilde değiştirme erişir ve bir bellek içi XML ağacı düğümler üzerinden gider kod yazın.</span><span class="sxs-lookup"><span data-stu-id="bf468-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="bf468-115">LINQ to XML ile her iki yöntemle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf468-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="bf468-116">Aynı sınıfları kullanın ve bazı durumlarda aynı yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bf468-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="bf468-117">Ancak, iki yaklaşım, hedefler ve yapısı çok farklıdır.</span><span class="sxs-lookup"><span data-stu-id="bf468-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="bf468-118">Örneğin, farklı durumlarda, bir ya da diğer bir yaklaşım genellikle daha iyi performans sunar ve daha fazla veya daha az bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf468-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="bf468-119">Ayrıca, bir ya da diğer bir yaklaşım yazma ve daha fazla sürdürülebilir kod yield daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf468-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="bf468-120">Karşıtlıklar iki yaklaşım için bkz [bellek içi XML ağacı değişikliği ve. İşlevsel oluşturma (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bf468-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="bf468-121">İşlevsel dönüşümlere yazma ilişkin bir öğretici için bkz. [saf işlevsel dönüşümleri XML (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="bf468-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf468-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf468-122">See also</span></span>

- [<span data-ttu-id="bf468-123">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="bf468-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
