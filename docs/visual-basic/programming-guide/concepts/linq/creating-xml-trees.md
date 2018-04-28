---
title: Oluşturma XML ağaçları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e86ba12b-17de-4579-81bb-66322b84cfbe
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08efc9a9b519d2b56f8503e050b9332be580d124
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="creating-xml-trees-visual-basic"></a><span data-ttu-id="cd13a-102">Oluşturma XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd13a-102">Creating XML Trees (Visual Basic)</span></span>
<span data-ttu-id="cd13a-103">En yaygın XML görevlerden birini bir XML ağacı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cd13a-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="cd13a-104">Bu bölümde, bunları oluşturmak için çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd13a-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd13a-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cd13a-105">In This Section</span></span>  
  
|<span data-ttu-id="cd13a-106">Konu</span><span class="sxs-lookup"><span data-stu-id="cd13a-106">Topic</span></span>|<span data-ttu-id="cd13a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd13a-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cd13a-108">İşlev yapımı (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd13a-108">Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="cd13a-109">İşlev yapısında genel bir bakış sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd13a-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="cd13a-110">İşlev oluşturma, XML ağacını bölümünü veya tümünü tek bir deyimde oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd13a-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="cd13a-111">Bu konu ayrıca sorguları bir XML ağacı oluşturulurken katıştırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd13a-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="cd13a-112">Visual Basic'de XML değişmez değerleri giriş</span><span class="sxs-lookup"><span data-stu-id="cd13a-112">Introduction to XML Literals in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)|<span data-ttu-id="cd13a-113">XML değişmez değerleri kullanarak Visual Basic'te ağaçları oluşturmanın hızlı bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd13a-113">Provides a quick introduction to creating trees in Visual Basic by using XML literals.</span></span> <span data-ttu-id="cd13a-114">Bu konuda XML değişmez değerleri Visual Basic belgeleri bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd13a-114">This topic includes links to the Visual Basic documentation of XML literals.</span></span>|  
|[<span data-ttu-id="cd13a-115">Kopyalama ve Düğmelere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd13a-115">Cloning vs. Attaching (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="cd13a-116">(Düğümler kopyalanabilen ve daha sonra eklenen) bir varolan XML ağacından düğüm ekleme ve üst (yalnızca takılı oldukları) yok düğüm ekleme arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd13a-116">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="cd13a-117">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd13a-117">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="cd13a-118">Çeşitli kaynaklardan gelen XML Ayrıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd13a-118">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="cd13a-119"> üzerinde katmanlı <xref:System.Xml.XmlReader>, XML ayrıştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd13a-119"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="cd13a-120">Nasıl yapılır: bir XmlWriter (LINQ-XML) içeren bir XML ağacı Doldur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd13a-120">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="cd13a-121">Kullanarak bir XML ağacı doldurmak nasıl gösterir bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="cd13a-121">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="cd13a-122">Nasıl yapılır: XSD (LINQ-XML) kullanarak doğrulayabilirsiniz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd13a-122">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="cd13a-123">XSD kullanarak bir XML ağacı doğrulanmasının nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd13a-123">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="cd13a-124">XElement ve XDocument Nesnelerinin Geçerli İçeriği</span><span class="sxs-lookup"><span data-stu-id="cd13a-124">Valid Content of XElement and XDocument Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects.md)|<span data-ttu-id="cd13a-125">Oluşturucular ve içerik öğelerini ve belgeleri eklemek için kullanılan yöntemleri geçirilen geçerli değişkenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd13a-125">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd13a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd13a-126">See Also</span></span>  
 [<span data-ttu-id="cd13a-127">Programlama Kılavuzu (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd13a-127">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
