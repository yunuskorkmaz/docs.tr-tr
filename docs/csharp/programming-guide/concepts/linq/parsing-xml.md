---
title: "XML Ayrıştırma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d262fd2177ac77ab5109362f94cc51d03c9563c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-xml-c"></a><span data-ttu-id="75200-102">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="75200-102">Parsing XML (C#)</span></span>
<span data-ttu-id="75200-103">Bu bölümdeki konular, XML belgelerini incelemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="75200-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75200-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="75200-104">In This Section</span></span>  
  
|<span data-ttu-id="75200-105">Konu</span><span class="sxs-lookup"><span data-stu-id="75200-105">Topic</span></span>|<span data-ttu-id="75200-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75200-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="75200-107">Nasıl yapılır: bir dize (C#) ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="75200-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="75200-108">Bir XML ağacı oluşturmak için bir dizesi ayrıştırılamıyor gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75200-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="75200-109">Nasıl yapılır: XML yükleme bir dosyadan (C#)</span><span class="sxs-lookup"><span data-stu-id="75200-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="75200-110">XML kullanarak bir URI yük gösterilmektedir <xref:System.Xml.Linq.XElement.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75200-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="75200-111">Beyaz alan yüklenirken veya XML Ayrıştırma sırasında koruma</span><span class="sxs-lookup"><span data-stu-id="75200-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="75200-112">Beyaz alan davranışını denetlemek açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları yüklenirken.</span><span class="sxs-lookup"><span data-stu-id="75200-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="75200-113">Nasıl yapılır: hatalar (C#) ayrıştırma Catch</span><span class="sxs-lookup"><span data-stu-id="75200-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="75200-114">Hatalı biçimlendirilmiş veya geçersiz XML algılamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75200-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="75200-115">Nasıl yapılır: bir ağaç XmlReader (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="75200-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="75200-116">Bir XML ağacından doğrudan oluşturmayı gösteren bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="75200-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="75200-117">Nasıl yapılır: akış parçalarını gelen XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="75200-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="75200-118">XML parçaları kullanarak akışı gösterilmektedir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="75200-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="75200-119">Büyük XML dosyalarını işlemek varsa, XML ağacın tamamı belleğe yüklemek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="75200-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="75200-120">Bunun yerine, XML parçaları akışını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75200-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75200-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75200-121">See Also</span></span>  
 [<span data-ttu-id="75200-122">Oluşturma XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="75200-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
