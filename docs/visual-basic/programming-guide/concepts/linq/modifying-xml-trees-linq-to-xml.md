---
title: "XML ağaçları (LINQ-XML) değiştirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de66788186f3ffd09560d8eacdebbbaa5edf067c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a><span data-ttu-id="62f65-102">XML ağaçları (LINQ-XML) değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f65-102">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="62f65-103">bir bellek içi bir XML şemasına deposudur.</span><span class="sxs-lookup"><span data-stu-id="62f65-103"> is an in-memory store for an XML tree.</span></span> <span data-ttu-id="62f65-104">Yüklenemiyor veya bir kaynak XML ağacından ayrıştırılamıyor sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yerinde ağacı değiştirmek ve belki de bir dosyaya kaydetmeyi veya uzak bir sunucuya gönderme ağaç seri hale olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="62f65-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="62f65-105">Yerinde bir ağaç değiştirdiğinizde, bazı yöntemler gibi kullandığınız <xref:System.Xml.Linq.XContainer.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="62f65-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="62f65-106">Ancak, işlevsel yapım yeni bir ağaç farklı bir şekilde oluşturmak için kullanılacak olan başka bir yaklaşım yoktur.</span><span class="sxs-lookup"><span data-stu-id="62f65-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="62f65-107">XML ağacına yapmanız gereken değişiklikleri türlerine bağlı ve ağaç boyutuna bağlı olarak bu yaklaşım, daha sağlam ve geliştirmek daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="62f65-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="62f65-108">İlk konu bu bölümde, bu iki yaklaşım karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="62f65-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62f65-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="62f65-109">In This Section</span></span>  
  
|<span data-ttu-id="62f65-110">Konu</span><span class="sxs-lookup"><span data-stu-id="62f65-110">Topic</span></span>|<span data-ttu-id="62f65-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62f65-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="62f65-112">Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f65-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|<span data-ttu-id="62f65-113">İşlev oluşturma için bellek XML ağacında değiştirme karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="62f65-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="62f65-114">Bir XML ağacına (Visual Basic) öğeleri, öznitelikleri ve düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="62f65-114">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="62f65-115">Öğe, öznitelik veya düğümleri bir XML ağacına ekleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="62f65-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="62f65-116">Öğeleri, öznitelikleri ve bir XML ağacında düğümlerin değiştirme</span><span class="sxs-lookup"><span data-stu-id="62f65-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="62f65-117">Varolan öğeleri, öznitelikleri veya düğümler değiştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="62f65-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="62f65-118">Öğeleri, öznitelikleri ve düğümler XML ağacından (Visual Basic) kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="62f65-118">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="62f65-119">XML ağacından öğeleri, öznitelikleri veya düğümleri kaldırma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="62f65-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="62f65-120">Bakımı ad/değer çiftleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f65-120">Maintaining Name/Value Pairs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="62f65-121">En iyi yapılandırma bilgileri veya genel ayarlar gibi ad/değer çiftleri olarak tutulur uygulama bilgilerini korumak açıklar.</span><span class="sxs-lookup"><span data-stu-id="62f65-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="62f65-122">Nasıl yapılır: bir tüm XML ağacı (Visual Basic) Namespace değiştirme</span><span class="sxs-lookup"><span data-stu-id="62f65-122">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="62f65-123">Bir XML ağacı bir ad alanından başka bir dosyaya taşıma gösterir.</span><span class="sxs-lookup"><span data-stu-id="62f65-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62f65-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62f65-124">See Also</span></span>  
 [<span data-ttu-id="62f65-125">Programlama Kılavuzu (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f65-125">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
