---
title: İşlevsel ve Yordamsal Programlama (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594254"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="3bb2b-102">İşlevsel ve Yordamsal Programlama (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3bb2b-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3bb2b-103">Çeşitli XML uygulamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="3bb2b-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="3bb2b-104">Bazı uygulamalar kaynak XML belgeleri alır ve kaynak belgelerden farklı bir biçimde yeni XML belgeleri üretir.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="3bb2b-105">Bazı uygulamalar kaynak XML belgeleri alır ve html veya CSV metin dosyaları gibi tamamen farklı bir biçimde sonuç belgeleri üretir.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="3bb2b-106">Bazı uygulamalar kaynak XML belgelerini alır ve kayıtları veritabanına ekler.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="3bb2b-107">Bazı uygulamalar veritabanı gibi başka bir kaynaktan veri alır ve bu kaynaktan XML belgeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="3bb2b-108">Bunlar XML uygulama türlerinin tümü değildir, ancak bunlar bir XML programcısının uygulamak zorunda olduğu işlevsellik türlerinin temsili kümesidir.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="3bb2b-109">Bu tür uygulamaların tümlerinde, bir geliştiricinin kaldırabileceği iki zıt yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="3bb2b-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="3bb2b-110">Bildirimsel bir yaklaşım la fonksiyonel yapı.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="3bb2b-111">Yordam kodu kullanarak bellek tesisi XML ağaç modifikasyonu.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="3bb2b-112">LINQ to XML her iki yaklaşımı da destekler.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="3bb2b-113">İşlevsel yaklaşımı kullanırken, kaynak belgeleri alan ve istenen şekille tamamen yeni sonuç belgeleri oluşturan dönüşümler yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="3bb2b-114">Bir XML ağacını yerinde değiştirirken, bellek içi bir XML ağacında düğümler arasında geçiş yapan ve gezinen kod yazar, düğümleri gerektiği gibi ekler, siler ve değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="3bb2b-115">Her iki yaklaşımla LINQ xml kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="3bb2b-116">Aynı sınıfları ve bazı durumlarda aynı yöntemleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="3bb2b-117">Ancak, iki yaklaşımın yapısı ve hedefleri çok farklıdır.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="3bb2b-118">Örneğin, farklı durumlarda, bir veya diğer yaklaşım genellikle daha iyi performansa sahip olacak ve daha fazla veya daha az bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="3bb2b-119">Buna ek olarak, bir veya diğer yaklaşım yazmak ve daha sadaabilir kod verim daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="3bb2b-120">Zıt iki yaklaşımı görmek için Bellek [Içi XML Ağaç Modifikasyonu ve Fonksiyonel Yapı (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3bb2b-121">İşlevsel dönüşümleri yazma konusunda bir öğretici için Bkz. [XML'in Saf İşlevsel Dönüşümleri (C#)](./introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="3bb2b-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb2b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bb2b-122">See also</span></span>

- [<span data-ttu-id="3bb2b-123">LINQ - XML Programlamaya Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="3bb2b-123">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
