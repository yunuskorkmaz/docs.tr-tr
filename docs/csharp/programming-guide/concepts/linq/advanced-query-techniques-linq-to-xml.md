---
title: "Gelişmiş sorgu teknikler (LINQ-XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 028d978e-215b-4d50-ba70-adce0659386d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5898813d5773f13fa2c969b065e5ab1412726e9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-query-techniques-linq-to-xml-c"></a><span data-ttu-id="56e8f-102">Gelişmiş sorgu teknikler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="56e8f-102">Advanced Query Techniques (LINQ to XML) (C#)</span></span>
<span data-ttu-id="56e8f-103">Bu bölümde daha gelişmiş örnekleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu teknikleri.</span><span class="sxs-lookup"><span data-stu-id="56e8f-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56e8f-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="56e8f-104">In This Section</span></span>  
  
|<span data-ttu-id="56e8f-105">Konu</span><span class="sxs-lookup"><span data-stu-id="56e8f-105">Topic</span></span>|<span data-ttu-id="56e8f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56e8f-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="56e8f-107">Nasıl yapılır: iki koleksiyonları (LINQ-XML) birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="56e8f-107">How to: Join Two Collections (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="56e8f-108">Nasıl kullanılacağını gösterir `Join` XML verilerinde ilişkileri yararlanmak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="56e8f-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="56e8f-109">Nasıl yapılır: gruplandırma (C#) kullanarak hiyerarşi oluşturma</span><span class="sxs-lookup"><span data-stu-id="56e8f-109">How to: Create Hierarchy Using Grouping (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="56e8f-110">Veri grubu ve XML gruplandırılması tabanlı oluşturmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56e8f-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="56e8f-111">Nasıl yapılır: LINQ-XML XPath (C#) kullanarak sorgulama</span><span class="sxs-lookup"><span data-stu-id="56e8f-111">How to: Query LINQ to XML Using XPath (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="56e8f-112">XPath sorguları temel alan koleksiyonlar almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="56e8f-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="56e8f-113">Nasıl yapılır: bir LINQ yazma XML eksen yöntemine (C#)</span><span class="sxs-lookup"><span data-stu-id="56e8f-113">How to: Write a LINQ to XML Axis Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="56e8f-114">Nasıl yazılacağını göstermektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksen yöntemi.</span><span class="sxs-lookup"><span data-stu-id="56e8f-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="56e8f-115">Nasıl yapılır: XML (C#) için metin akış dönüştürmeleri gerçekleştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="56e8f-115">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transformations-of-text-to-xml.md)|<span data-ttu-id="56e8f-116">Küçük bellek alanını korurken çok büyük boyutlu metin dosyalarını XML'e dönüştürmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="56e8f-116">Shows how to transform very large text files into XML while maintaining a small memory footprint.</span></span>|  
|[<span data-ttu-id="56e8f-117">Nasıl yapılır: bir ağaç (C#) tüm düğümler listesi</span><span class="sxs-lookup"><span data-stu-id="56e8f-117">How to: List All Nodes in a Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="56e8f-118">Bir XML ağacındaki tüm düğümleri listeler bir yardımcı program yöntemi sunar.</span><span class="sxs-lookup"><span data-stu-id="56e8f-118">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="56e8f-119">Bu, bir XML ağacı değiştiren kodda hata ayıklama için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="56e8f-119">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="56e8f-120">Nasıl yapılır: almak paragrafları Office Açık XML belgesinden (C#)</span><span class="sxs-lookup"><span data-stu-id="56e8f-120">How to: Retrieve Paragraphs from an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="56e8f-121">Office Açık XML belgesi açıldığında, paragrafları XElement nesneler koleksiyonunu, paragraf metnini ve paragrafları stilini alır kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="56e8f-121">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="56e8f-122">Nasıl yapılır: Office Açık XML belgesi (C#) değiştirme</span><span class="sxs-lookup"><span data-stu-id="56e8f-122">How to: Modify an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="56e8f-123">Açılır, değiştirir ve Office Açık XML belgesi kaydeden kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="56e8f-123">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="56e8f-124">Nasıl yapılır: dosya sistemi (C#) XML ağacından doldurma</span><span class="sxs-lookup"><span data-stu-id="56e8f-124">How to: Populate an XML Tree from the File System (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="56e8f-125">Dosya sisteminden bir XML ağacı oluşturan kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="56e8f-125">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56e8f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56e8f-126">See Also</span></span>  
 [<span data-ttu-id="56e8f-127">Sorgulama XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="56e8f-127">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
