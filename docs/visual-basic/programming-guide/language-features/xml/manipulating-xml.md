---
title: XML düzenleme
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
ms.openlocfilehash: bb5aed5099d81f8c8898cd61523b90a43f27db78
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636165"
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="56347-102">Visual Basic'de XML'i Düzenleme</span><span class="sxs-lookup"><span data-stu-id="56347-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="56347-103">XML *değişmez* değerlerini dize, dosya veya akış gibi bir dış kaynaktan XML yüklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56347-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="56347-104">Ardından, XML 'yi işlemek için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanabilir ve XML 'yi sorgulamak için dil ile tümleşik sorgu (LINQ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56347-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use Language-Integrated Query (LINQ) to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56347-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="56347-105">In This Section</span></span>  
 [<span data-ttu-id="56347-106">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme</span><span class="sxs-lookup"><span data-stu-id="56347-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="56347-107">Bir metin dosyası, dize veya akıştan XML 'nin bir <xref:System.Xml.Linq.XDocument> veya <xref:System.Xml.Linq.XElement> nesnesine nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="56347-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="56347-108">Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="56347-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="56347-109">Bir <xref:System.Xml.Linq.XDocument> nesnesinin içeriğinin yeni bir XML belgesine nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="56347-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="56347-110">Nasıl yapılır: XML Değişmez Değerlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="56347-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="56347-111">Bir XML sabit değerinde öğelerin, özniteliklerin ve değerlerin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="56347-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="56347-112">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="56347-112">Related Sections</span></span>  
 [<span data-ttu-id="56347-113">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="56347-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="56347-114">Çeşitli XML erişimi özelliklerini tanımlayan bölümlere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="56347-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="56347-115">Visual Basic LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="56347-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="56347-116">Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımı için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="56347-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="56347-117">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="56347-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="56347-118">Visual Basic XML sabit değerlerini kullanmaya giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="56347-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="56347-119">Visual Basic XML 'e erişme</span><span class="sxs-lookup"><span data-stu-id="56347-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="56347-120">Visual Basic bir XML öğesinin veya belgenin bölümlerine nasıl erişileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="56347-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="56347-121">XML</span><span class="sxs-lookup"><span data-stu-id="56347-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="56347-122">Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımını betimleyen bölümlere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="56347-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56347-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56347-123">See also</span></span>

- [<span data-ttu-id="56347-124">XML</span><span class="sxs-lookup"><span data-stu-id="56347-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="56347-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="56347-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="56347-126">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="56347-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
