---
title: XML Ayrıştırma (C#)
ms.date: 07/20/2015
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
ms.openlocfilehash: f19e5a316621262bfe0f3fb56a13275336cf763f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617050"
---
# <a name="parsing-xml-c"></a><span data-ttu-id="2d1a2-102">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="2d1a2-102">Parsing XML (C#)</span></span>
<span data-ttu-id="2d1a2-103">Bu bölümdeki konular, XML belgelerini ayrıştırmak kullanılan nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d1a2-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2d1a2-104">In This Section</span></span>  
  
|<span data-ttu-id="2d1a2-105">Konu</span><span class="sxs-lookup"><span data-stu-id="2d1a2-105">Topic</span></span>|<span data-ttu-id="2d1a2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d1a2-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2d1a2-107">Nasıl yapılır: Bir dizeyi ayrıştırmak (C#)</span><span class="sxs-lookup"><span data-stu-id="2d1a2-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="2d1a2-108">Bir XML ağacı oluşturmak için bir dizeyi ayrıştırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="2d1a2-109">Nasıl yapılır: Bir dosyadan XML yükleme (C#)</span><span class="sxs-lookup"><span data-stu-id="2d1a2-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="2d1a2-110">XML kullanarak bir URI yüklemeyi gösterir <xref:System.Xml.Linq.XElement.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="2d1a2-111">XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma</span><span class="sxs-lookup"><span data-stu-id="2d1a2-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="2d1a2-112">Boşluk davranışını denetlemek nasıl açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçlarını yüklenirken.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="2d1a2-113">Nasıl yapılır: Ayrıştırma hatalarını yakalama (C#)</span><span class="sxs-lookup"><span data-stu-id="2d1a2-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="2d1a2-114">Hatalı biçimlendirilmiş veya geçersiz XML nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="2d1a2-115">Nasıl yapılır: Xmlreader'dan ağaç oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="2d1a2-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="2d1a2-116">Bir XML ağacı doğrudan nasıl oluşturulacağını gösterir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="2d1a2-117">Nasıl yapılır: Stream xmlreader'dan XML parçalarının (C#)</span><span class="sxs-lookup"><span data-stu-id="2d1a2-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="2d1a2-118">Kullanarak XML parçalarının akışını yapma hakkında gösteren bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="2d1a2-119">Büyük XML dosyalarını işlemek varsa, tüm XML ağacının belleğe yüklemek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="2d1a2-120">Bunun yerine, XML parçalarının akışını yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d1a2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d1a2-121">See also</span></span>

- [<span data-ttu-id="2d1a2-122">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="2d1a2-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
