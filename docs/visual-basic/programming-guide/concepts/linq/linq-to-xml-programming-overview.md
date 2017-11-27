---
title: "LINQ-XML programlamaya genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7c07d0a-1fae-4610-ae51-56dd7075cc14
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 84816fe2c75d59a8bc4a7cb93d1f87974eaf17b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-programming-overview-visual-basic"></a><span data-ttu-id="c2d32-102">LINQ-XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-102">LINQ to XML Programming Overview (Visual Basic)</span></span>
<span data-ttu-id="c2d32-103">Bu konular hakkında üst düzey genel bakış bilgileri sağlar. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları, ayrıntılı bilgiler yanı sıra en önemli sınıfların üç.</span><span class="sxs-lookup"><span data-stu-id="c2d32-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2d32-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c2d32-104">In This Section</span></span>  
  
|<span data-ttu-id="c2d32-105">Konu</span><span class="sxs-lookup"><span data-stu-id="c2d32-105">Topic</span></span>|<span data-ttu-id="c2d32-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2d32-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c2d32-107">İşlev vs. Yordam programlama (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-107">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="c2d32-108">LINQ XML uygulamaları yazmak için iki ilkesine yaklaşım yüksek düzey bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2d32-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="c2d32-109">LINQ-XML sınıfları genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-109">LINQ to XML Classes Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="c2d32-110">Genel bir bakış sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c2d32-110">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes.</span></span>|  
|[<span data-ttu-id="c2d32-111">XElement sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-111">XElement Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="c2d32-112">Tanıtır <xref:System.Xml.Linq.XElement> XML öğeleri temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="c2d32-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="c2d32-113"><xref:System.Xml.Linq.XElement>temel sınıflar biri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıf hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="c2d32-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="c2d32-114">XAttribute sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-114">XAttribute Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="c2d32-115">Tanıtır <xref:System.Xml.Linq.XAttribute> XML öznitelikleri temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="c2d32-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="c2d32-116">XDocument sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-116">XDocument Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="c2d32-117">Tanıtır <xref:System.Xml.Linq.XDocument> XML belgeleri temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="c2d32-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="c2d32-118">Nasıl yapılır: derleme LINQ-XML örnekleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-118">How to: Build LINQ to XML Examples (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="c2d32-119">İçeren `Imports` LINQ-XML örnekleri oluşturmak için gerekli deyimleri.</span><span class="sxs-lookup"><span data-stu-id="c2d32-119">Contains the `Imports` statements that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2d32-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2d32-120">See Also</span></span>  
 [<span data-ttu-id="c2d32-121">Programlama Kılavuzu (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2d32-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
