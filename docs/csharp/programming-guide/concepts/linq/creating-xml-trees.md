---
title: "Oluşturma XML ağaçları (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bccc3e0a-c08c-468e-9d30-e075670fdace
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23b19593774b5a010b453e3fe755e21386afd015
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-trees-c"></a><span data-ttu-id="e3653-102">Oluşturma XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="e3653-102">Creating XML Trees (C#)</span></span>
<span data-ttu-id="e3653-103">En yaygın XML görevlerden birini bir XML ağacı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e3653-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="e3653-104">Bu bölümde, bunları oluşturmak için çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3653-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3653-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e3653-105">In This Section</span></span>  
  
|<span data-ttu-id="e3653-106">Konu</span><span class="sxs-lookup"><span data-stu-id="e3653-106">Topic</span></span>|<span data-ttu-id="e3653-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3653-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e3653-108">İşlev yapımı (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e3653-108">Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="e3653-109">İşlev yapısında genel bir bakış sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3653-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="e3653-110">İşlev oluşturma, XML ağacını bölümünü veya tümünü tek bir deyimde oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3653-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="e3653-111">Bu konu ayrıca sorguları bir XML ağacı oluşturulurken katıştırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3653-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="e3653-112">C# (LINQ-XML) XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3653-112">Creating XML Trees in C# (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)|<span data-ttu-id="e3653-113">Ağaçları C# ' ta oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3653-113">Shows how to create trees in C#.</span></span>|  
|[<span data-ttu-id="e3653-114">Kopyalama vs. Ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="e3653-114">Cloning vs. Attaching (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="e3653-115">(Düğümler kopyalanabilen ve daha sonra eklenen) bir varolan XML ağacından düğüm ekleme ve üst (yalnızca takılı oldukları) yok düğüm ekleme arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3653-115">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="e3653-116">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="e3653-116">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="e3653-117">Çeşitli kaynaklardan gelen XML Ayrıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e3653-117">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e3653-118">üzerinde katmanlı <xref:System.Xml.XmlReader>, XML ayrıştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3653-118"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="e3653-119">Nasıl yapılır: bir XmlWriter (LINQ-XML) içeren bir XML ağacı Doldur (C#)</span><span class="sxs-lookup"><span data-stu-id="e3653-119">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="e3653-120">Kullanarak bir XML ağacı doldurmak nasıl gösterir bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="e3653-120">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="e3653-121">Nasıl yapılır: XSD (LINQ-XML) kullanarak doğrulayabilirsiniz (C#)</span><span class="sxs-lookup"><span data-stu-id="e3653-121">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="e3653-122">XSD kullanarak bir XML ağacı doğrulanmasının nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3653-122">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="e3653-123">Geçerli içerik XElement ve XDocument nesneleri</span><span class="sxs-lookup"><span data-stu-id="e3653-123">Valid Content of XElement and XDocument Objects</span></span>](../../../../csharp/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects3.md)|<span data-ttu-id="e3653-124">Oluşturucular ve içerik öğelerini ve belgeleri eklemek için kullanılan yöntemleri geçirilen geçerli değişkenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3653-124">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3653-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3653-125">See Also</span></span>  
 [<span data-ttu-id="e3653-126">Programlama Kılavuzu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e3653-126">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
