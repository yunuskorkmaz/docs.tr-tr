---
title: "Ad alanları genel bakış (LINQ-XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 082172720abd39634f7183367d4d7b8d53d2bb7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-overview-linq-to-xml"></a><span data-ttu-id="78411-102">Ad alanları genel bakış (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="78411-102">Namespaces Overview (LINQ to XML)</span></span>
<span data-ttu-id="78411-103">Ad alanları, bu konu tanıtır <xref:System.Xml.Linq.XName> sınıfı ve <xref:System.Xml.Linq.XNamespace> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="78411-103">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>  
  
## <a name="xml-names"></a><span data-ttu-id="78411-104">XML adları</span><span class="sxs-lookup"><span data-stu-id="78411-104">XML Names</span></span>  
 <span data-ttu-id="78411-105">XML genellikle bir kaynak XML programlamada karmaşıklık adlardır.</span><span class="sxs-lookup"><span data-stu-id="78411-105">XML names are often a source of complexity in XML programming.</span></span> <span data-ttu-id="78411-106">Bir XML adı (bir XML ad alanı URI'si olarak da bilinir) bir XML ad alanı ve yerel ad oluşur.</span><span class="sxs-lookup"><span data-stu-id="78411-106">An XML name consists of an XML namespace (also called an XML namespace URI) and a local name.</span></span> <span data-ttu-id="78411-107">Bir XML ad alanı için bir ad alanındaki benzer bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-tabanlı programı.</span><span class="sxs-lookup"><span data-stu-id="78411-107">An XML namespace is similar to a namespace in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-based program.</span></span> <span data-ttu-id="78411-108">Öğeleri ve özniteliklerinin adları benzersiz olarak nitelemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="78411-108">It enables you to uniquely qualify the names of elements and attributes.</span></span> <span data-ttu-id="78411-109">Bu, bir XML belgesi çeşitli kısımlarını arasındaki ad çakışmalarının önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="78411-109">This helps avoid name conflicts between various parts of an XML document.</span></span> <span data-ttu-id="78411-110">Bir XML ad alanı bildirirken yalnızca ad alanında benzersiz olması için bir yerel adı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78411-110">When you have declared an XML namespace, you can select a local name that only has to be unique within that namespace.</span></span>  
  
 <span data-ttu-id="78411-111">Başka bir XML adları XML yönüdür *ad alanı öneklerini*.</span><span class="sxs-lookup"><span data-stu-id="78411-111">Another aspect of XML names is XML *namespace prefixes*.</span></span> <span data-ttu-id="78411-112">XML öneklerini XML adları karmaşıklığını çoğunu neden.</span><span class="sxs-lookup"><span data-stu-id="78411-112">XML prefixes cause most of the complexity of XML names.</span></span> <span data-ttu-id="78411-113">Bu önekler XML belge daha kısa ve anlaşılabilir hale getirir bir XML ad alanı için bir kısayol oluşturmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="78411-113">These prefixes enable you to create a shortcut for an XML namespace, which makes the XML document more concise and understandable.</span></span> <span data-ttu-id="78411-114">Ancak, XML öneklerini karmaşıklık ekler anlamı sağlamak için bunların içeriğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="78411-114">However, XML prefixes depend on their context to have meaning, which adds complexity.</span></span> <span data-ttu-id="78411-115">Örneğin, XML öneki `aw` XML ağacının bir parçası olarak bir XML ad alanı ve farklı bir XML ad alanı XML ağacının farklı bir parçası olarak ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="78411-115">For example, the XML prefix `aw` could be associated with one XML namespace in one part of an XML tree, and with a different XML namespace in a different part of the XML tree.</span></span>  
  
 <span data-ttu-id="78411-116">Kullanırken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic ve XML değişmez değerleri ile ad alanı öneklerini ad alanları belgelerle çalışırken kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="78411-116">When using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with Visual Basic and XML literals, you must use namespace prefixes when working with documents in namespaces.</span></span>  
  
 <span data-ttu-id="78411-117">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML adlarını temsil eden sınıf <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="78411-117">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the class that represents XML names is <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="78411-118">XML adları görünür sık boyunca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, bir XML adı gerekli olduğu yerlerde bulacaktır bir <xref:System.Xml.Linq.XName> parametresi.</span><span class="sxs-lookup"><span data-stu-id="78411-118">XML names appear frequently throughout the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, and wherever an XML name is required, you will find an <xref:System.Xml.Linq.XName> parameter.</span></span> <span data-ttu-id="78411-119">Ancak, nadiren doğrudan birlikte çalıştığınız bir <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="78411-119">However, you rarely work directly with an <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="78411-120"><xref:System.Xml.Linq.XName>dize örtük bir dönüştürme içerir.</span><span class="sxs-lookup"><span data-stu-id="78411-120"><xref:System.Xml.Linq.XName> contains an implicit conversion from string.</span></span>  
  
 <span data-ttu-id="78411-121">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="78411-121">For more information, see <xref:System.Xml.Linq.XNamespace> and <xref:System.Xml.Linq.XName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78411-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78411-122">See Also</span></span>  
 [<span data-ttu-id="78411-123">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="78411-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
