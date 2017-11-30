---
title: "Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81172ebb440bc2737bbe3f1de0f1dd3cf6e086c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="dc595-102">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dc595-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="dc595-103">Bu bölümde örnekleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tahminleri ve dönüştürmeler.</span><span class="sxs-lookup"><span data-stu-id="dc595-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc595-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dc595-104">In This Section</span></span>  
  
|<span data-ttu-id="dc595-105">Konu</span><span class="sxs-lookup"><span data-stu-id="dc595-105">Topic</span></span>|<span data-ttu-id="dc595-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc595-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dc595-107">Nasıl yapılır: LINQ-XML (C#) kullanarak sözlükler ile çalışma</span><span class="sxs-lookup"><span data-stu-id="dc595-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="dc595-108">Sözlükler XML dönüştürme etme ve sözlükler XML dönüştürme gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc595-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="dc595-109">Nasıl yapılır: bir XML ağacının (C#) şekil Dönüştür</span><span class="sxs-lookup"><span data-stu-id="dc595-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="dc595-110">Bir XML belgesi şeklini dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc595-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="dc595-111">Nasıl yapılır: bir yansıtma (C#) türünü denetlemek</span><span class="sxs-lookup"><span data-stu-id="dc595-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="dc595-112">Denetlemenize gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="dc595-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="dc595-113">Nasıl yapılır: Proje yeni türü (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dc595-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="dc595-114">Kullanıcı tanımlı bir türünden koleksiyonu proje gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="dc595-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="dc595-115">Nasıl yapılır: Proje bir nesne grafiğinin (C#)</span><span class="sxs-lookup"><span data-stu-id="dc595-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="dc595-116">Daha karmaşık bir nesne grafikten proje gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="dc595-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="dc595-117">Nasıl yapılır: Proje anonim bir tür (C#)</span><span class="sxs-lookup"><span data-stu-id="dc595-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="dc595-118">Anonim nesneleri koleksiyonu proje gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="dc595-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="dc595-119">Nasıl yapılır: metin dosyaları oluşturmak XML'den (C#)</span><span class="sxs-lookup"><span data-stu-id="dc595-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="dc595-120">Bir XML olmayan metin dosyasını bir XML dosyasına dönüştürmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc595-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="dc595-121">Nasıl yapılır: XML CSV dosyalarından (C#) oluştur</span><span class="sxs-lookup"><span data-stu-id="dc595-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="dc595-122">Nasıl kullanılacağını gösterir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir CSV dosyasını ayrıştırabilir ve XML oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="dc595-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc595-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc595-123">See Also</span></span>  
 [<span data-ttu-id="dc595-124">Sorgulama XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="dc595-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
