---
title: "XML ağaçları (LINQ-XML) değiştirme (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8cf3ffabeb7c3caa5f0e3e38fb6f69551ce791b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a><span data-ttu-id="d8a5e-102">XML ağaçları (LINQ-XML) değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="d8a5e-102">Modifying XML Trees (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d8a5e-103">bir bellek içi bir XML şemasına deposudur.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-103"> is an in-memory store for an XML tree.</span></span> <span data-ttu-id="d8a5e-104">Yüklenemiyor veya bir kaynak XML ağacından ayrıştırılamıyor sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yerinde ağacı değiştirmek ve belki de bir dosyaya kaydetmeyi veya uzak bir sunucuya gönderme ağaç seri hale olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="d8a5e-105">Yerinde bir ağaç değiştirdiğinizde, bazı yöntemler gibi kullandığınız <xref:System.Xml.Linq.XContainer.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="d8a5e-106">Ancak, işlevsel yapım yeni bir ağaç farklı bir şekilde oluşturmak için kullanılacak olan başka bir yaklaşım yoktur.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="d8a5e-107">XML ağacına yapmanız gereken değişiklikleri türlerine bağlı ve ağaç boyutuna bağlı olarak bu yaklaşım, daha sağlam ve geliştirmek daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="d8a5e-108">İlk konu bu bölümde, bu iki yaklaşım karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8a5e-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d8a5e-109">In This Section</span></span>  
  
|<span data-ttu-id="d8a5e-110">Konu</span><span class="sxs-lookup"><span data-stu-id="d8a5e-110">Topic</span></span>|<span data-ttu-id="d8a5e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8a5e-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d8a5e-112">Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8a5e-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|<span data-ttu-id="d8a5e-113">İşlev oluşturma için bellek XML ağacında değiştirme karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="d8a5e-114">Bir XML ağacına (C#) öğeleri, öznitelikleri ve düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="d8a5e-114">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="d8a5e-115">Öğe, öznitelik veya düğümleri bir XML ağacına ekleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="d8a5e-116">Öğeleri, öznitelikleri ve bir XML ağacında düğümlerin değiştirme</span><span class="sxs-lookup"><span data-stu-id="d8a5e-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="d8a5e-117">Varolan öğeleri, öznitelikleri veya düğümler değiştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="d8a5e-118">Bir XML ağacından (C#) öğeleri, öznitelikleri ve düğümleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="d8a5e-118">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="d8a5e-119">XML ağacından öğeleri, öznitelikleri veya düğümleri kaldırma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="d8a5e-120">Bakımı ad/değer çiftleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d8a5e-120">Maintaining Name/Value Pairs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="d8a5e-121">En iyi yapılandırma bilgileri veya genel ayarlar gibi ad/değer çiftleri olarak tutulur uygulama bilgilerini korumak açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="d8a5e-122">Nasıl yapılır: Namespace değiştirmek için tüm XML ağacı (C#)</span><span class="sxs-lookup"><span data-stu-id="d8a5e-122">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="d8a5e-123">Bir XML ağacı bir ad alanından başka bir dosyaya taşıma gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8a5e-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-124">See Also</span></span>  
 [<span data-ttu-id="d8a5e-125">Programlama Kılavuzu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8a5e-125">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
