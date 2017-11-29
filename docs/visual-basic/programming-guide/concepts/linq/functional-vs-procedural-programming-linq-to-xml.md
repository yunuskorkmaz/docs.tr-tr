---
title: "İşlev vs. Yordam programlama (LINQ-XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e47ff583146ab4258e219537cdc01821009e965
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="a65fa-102">İşlev vs. Yordam programlama (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a65fa-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a65fa-103">XML uygulamaları çeşitli türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a65fa-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="a65fa-104">Bazı uygulamalar kaynak XML belgelerini almak ve kaynak belgeleri değerinden farklı bir şeklinde olan yeni XML belgeleri oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="a65fa-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="a65fa-105">Bazı uygulamalar kaynak XML belgelerini ayırın ve HTML veya CSV metin dosyaları gibi tamamen farklı bir form sonuç belgelerde üretir.</span><span class="sxs-lookup"><span data-stu-id="a65fa-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="a65fa-106">Bazı uygulamalar kaynak XML belgelerini almak ve bir veritabanına kayıtları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a65fa-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="a65fa-107">Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri almak ve XML belgeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a65fa-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="a65fa-108">Bu tüm XML uygulama türlerini değildir, ancak bunlar temsilcisi uygulamak için bir XML Programcı sahip işlevselliği türlerini kümesidir.</span><span class="sxs-lookup"><span data-stu-id="a65fa-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="a65fa-109">Tüm bu tür uygulamalar, bir geliştirici sürebilir karşıt iki yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="a65fa-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="a65fa-110">Bildirim temelli bir yaklaşım kullanarak işlev oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a65fa-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="a65fa-111">Bellek içi XML ağaç değişikliği yordam kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a65fa-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="a65fa-112">LINQ-XML her iki yaklaşımın destekler.</span><span class="sxs-lookup"><span data-stu-id="a65fa-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="a65fa-113">İşlev yaklaşımı kullanarak, kaynak belgeleri yapan ve oluşturmak istediğiniz şekli tamamen yeni sonuç belgelerle dönüşümleri yazma.</span><span class="sxs-lookup"><span data-stu-id="a65fa-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="a65fa-114">Bir XML ağacı yerinde değiştirirken, ekleme, silme ve gerektiğinde düğümleri değiştirme erişir ve bir bellek içi XML ağacında düğümler üzerinden gider kod yazın.</span><span class="sxs-lookup"><span data-stu-id="a65fa-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="a65fa-115">LINQ-XML her iki yaklaşım ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a65fa-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="a65fa-116">Aynı sınıflarını kullanın ve bazı durumlarda aynı yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a65fa-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="a65fa-117">Ancak, iki yaklaşım, hedefler ve yapısı çok farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="a65fa-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="a65fa-118">Örneğin, farklı durumlarda bir ya da bir yaklaşım genellikle daha iyi performans sahip ve fazla veya az bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="a65fa-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="a65fa-119">Ayrıca, bir ya da bir yaklaşım yazmak ve daha fazla Bakımı yapılabilir kodu elde etmek daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a65fa-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="a65fa-120">Contrasted iki yaklaşım görmek için bkz: [bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="a65fa-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="a65fa-121">İşlev dönüşümleri yazma bir öğretici için bkz: [saf işlevsel dönüşümleri XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a65fa-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65fa-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a65fa-122">See Also</span></span>  
 [<span data-ttu-id="a65fa-123">LINQ-XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a65fa-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
