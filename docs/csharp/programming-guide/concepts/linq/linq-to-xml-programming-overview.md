---
title: "LINQ-XML programlamaya genel bakış (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2dfa9b6f-5890-461d-b81c-316853c7f320
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4306be3540577bf921eff71dbd9dd822707b33dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-programming-overview-c"></a><span data-ttu-id="f2511-102">LINQ-XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-102">LINQ to XML Programming Overview (C#)</span></span>
<span data-ttu-id="f2511-103">Bu konular hakkında üst düzey genel bakış bilgileri sağlar. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları, ayrıntılı bilgiler yanı sıra en önemli sınıfların üç.</span><span class="sxs-lookup"><span data-stu-id="f2511-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2511-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f2511-104">In This Section</span></span>  
  
|<span data-ttu-id="f2511-105">Konu</span><span class="sxs-lookup"><span data-stu-id="f2511-105">Topic</span></span>|<span data-ttu-id="f2511-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2511-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f2511-107">İşlev vs. Yordam programlama (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-107">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="f2511-108">LINQ XML uygulamaları yazmak için iki ilkesine yaklaşım yüksek düzey bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2511-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="f2511-109">LINQ-XML sınıfları genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-109">LINQ to XML Classes Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="f2511-110">Genel bir bakış sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f2511-110">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes.</span></span>|  
|[<span data-ttu-id="f2511-111">XElement sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-111">XElement Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="f2511-112">Tanıtır <xref:System.Xml.Linq.XElement> XML öğeleri temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="f2511-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="f2511-113"><xref:System.Xml.Linq.XElement>temel sınıflar biri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıf hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="f2511-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="f2511-114">XAttribute sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-114">XAttribute Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="f2511-115">Tanıtır <xref:System.Xml.Linq.XAttribute> XML öznitelikleri temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="f2511-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="f2511-116">XDocument sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-116">XDocument Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="f2511-117">Tanıtır <xref:System.Xml.Linq.XDocument> XML belgeleri temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="f2511-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="f2511-118">Nasıl yapılır: derleme LINQ-XML örnekleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-118">How to: Build LINQ to XML Examples (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="f2511-119">İçeren `Using` LINQ-XML örnekleri oluşturmak için gerekli yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="f2511-119">Contains the `Using` directives that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2511-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2511-120">See Also</span></span>  
 [<span data-ttu-id="f2511-121">Programlama Kılavuzu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f2511-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
