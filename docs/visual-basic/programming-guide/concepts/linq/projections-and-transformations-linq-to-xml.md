---
title: "Projeksiyonlar ve dönüştürmeler (LINQ-XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 297de224-b625-44cf-8c00-186b6189aa0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92179ce3f1919187038b1bf7be92a82c1b6483ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-visual-basic"></a><span data-ttu-id="f79db-102">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79db-102">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f79db-103">Bu bölümde örnekleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tahminleri ve dönüştürmeler.</span><span class="sxs-lookup"><span data-stu-id="f79db-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f79db-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f79db-104">In This Section</span></span>  
  
|<span data-ttu-id="f79db-105">Konu</span><span class="sxs-lookup"><span data-stu-id="f79db-105">Topic</span></span>|<span data-ttu-id="f79db-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f79db-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f79db-107">Nasıl yapılır: LINQ-XML (Visual Basic) kullanarak sözlükler ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f79db-107">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="f79db-108">Sözlükler XML dönüştürme etme ve sözlükler XML dönüştürme gösterir.</span><span class="sxs-lookup"><span data-stu-id="f79db-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="f79db-109">Nasıl yapılır: bir XML ağacının (Visual Basic) şekil Dönüştür</span><span class="sxs-lookup"><span data-stu-id="f79db-109">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="f79db-110">Bir XML belgesi şeklini dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f79db-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="f79db-111">Nasıl yapılır: denetlemenize projeksiyonunun (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79db-111">How to: Control the Type of a Projection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="f79db-112">Denetlemenize gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="f79db-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f79db-113">Nasıl yapılır: Proje yeni türü (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79db-113">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="f79db-114">Kullanıcı tanımlı bir türünden koleksiyonu proje gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="f79db-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f79db-115">Nasıl yapılır: Proje bir nesne grafiğinin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79db-115">How to: Project an Object Graph (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="f79db-116">Daha karmaşık bir nesne grafikten proje gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="f79db-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f79db-117">Nasıl yapılır: Proje anonim bir türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79db-117">How to: Project an Anonymous Type (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="f79db-118">Anonim nesneleri koleksiyonu proje gösterilmektedir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="f79db-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f79db-119">Nasıl yapılır: metin dosyaları (Visual Basic) XML'den oluştur</span><span class="sxs-lookup"><span data-stu-id="f79db-119">How to: Generate Text Files from XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="f79db-120">Bir XML olmayan metin dosyasını bir XML dosyasına dönüştürmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f79db-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="f79db-121">Nasıl yapılır: XML (Visual Basic) CSV dosyalarından oluştur</span><span class="sxs-lookup"><span data-stu-id="f79db-121">How to: Generate XML from CSV Files (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="f79db-122">Nasıl kullanılacağını gösterir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir CSV dosyasını ayrıştırabilir ve XML oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f79db-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f79db-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f79db-123">See Also</span></span>  
 [<span data-ttu-id="f79db-124">Sorgulama XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79db-124">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
