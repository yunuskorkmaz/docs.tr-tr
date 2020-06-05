---
title: İşlevsel ve Yordam Programlama Karşılaştırması (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398441"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="8ed58-102">İşlevsel ve yordamsal programlama (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ed58-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8ed58-103">Çeşitli türlerdeki XML uygulamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="8ed58-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="8ed58-104">Bazı uygulamalar kaynak XML belgelerini alır ve kaynak belgelerden farklı bir şekilde yeni XML belgeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ed58-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="8ed58-105">Bazı uygulamalar kaynak XML belgelerini alır ve sonuç belgelerini HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ed58-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="8ed58-106">Bazı uygulamalar kaynak XML belgelerini alır ve bir veritabanına kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="8ed58-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="8ed58-107">Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri alır ve bundan XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ed58-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="8ed58-108">Bunlar, XML uygulaması türlerinin hepsi değildir, ancak bunlar bir XML Programlayıcısının uygulamak zorunda olduğu işlevsellik türlerinin temsili bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="8ed58-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="8ed58-109">Bu tür uygulamaların tümünde, bir geliştiricinin uygulayabileceğiniz iki yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="8ed58-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="8ed58-110">Bildirim temelli bir yaklaşım kullanılarak işlevsel oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8ed58-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="8ed58-111">Yordamsal kodu kullanarak bellek içi XML ağacı değişikliği.</span><span class="sxs-lookup"><span data-stu-id="8ed58-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="8ed58-112">LINQ to XML her iki yaklaşımı destekler.</span><span class="sxs-lookup"><span data-stu-id="8ed58-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="8ed58-113">İşlevsel yaklaşımı kullanırken, kaynak belgeleri alan ve istenen şekle sahip tamamen yeni sonuç belgeleri oluşturan dönüşümler yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="8ed58-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="8ed58-114">Bir XML ağacını yerinde değiştirirken, düğüm içi bir XML ağacındaki düğümlerde geçen ve gezinen, düğümleri ekleme, silme ve değiştirme gibi bir kod yazın.</span><span class="sxs-lookup"><span data-stu-id="8ed58-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="8ed58-115">LINQ to XML iki yaklaşımla de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ed58-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="8ed58-116">Aynı sınıfları ve bazı durumlarda aynı yöntemleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8ed58-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="8ed58-117">Ancak, iki yaklaşımdan oluşan yapı ve hedefler çok farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8ed58-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="8ed58-118">Örneğin, farklı durumlarda, bir veya diğer yaklaşım genellikle daha iyi performansa sahip olur ve daha fazla veya daha az bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ed58-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="8ed58-119">Buna ek olarak, bir veya başka bir yaklaşım daha fazla erişilebilir kod yazmak ve sağlamak daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8ed58-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="8ed58-120">Bu iki yaklaşımı görmek için bkz. [bellek ıçı XML ağacı değişikliği ve Işlevsel oluşturma (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="8ed58-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="8ed58-121">İşlev dönüştürmeleri yazma hakkında bir öğretici için bkz. [XML 'In saf Işlevsel dönüştürmeleri (Visual Basic)](pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8ed58-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed58-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ed58-122">See also</span></span>

- [<span data-ttu-id="8ed58-123">LINQ to XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ed58-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
