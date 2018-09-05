---
title: XML Ayrıştırma (C#)
ms.date: 07/20/2015
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
ms.openlocfilehash: a2dc3043c8cbf8138a164ab06d8394e4c859fa50
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523034"
---
# <a name="parsing-xml-c"></a><span data-ttu-id="9480e-102">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="9480e-102">Parsing XML (C#)</span></span>
<span data-ttu-id="9480e-103">Bu bölümdeki konular, XML belgelerini ayrıştırmak kullanılan nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9480e-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9480e-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9480e-104">In This Section</span></span>  
  
|<span data-ttu-id="9480e-105">Konu</span><span class="sxs-lookup"><span data-stu-id="9480e-105">Topic</span></span>|<span data-ttu-id="9480e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9480e-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9480e-107">Nasıl yapılır: bir dize (C#) ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="9480e-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="9480e-108">Bir XML ağacı oluşturmak için bir dizeyi ayrıştırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9480e-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="9480e-109">Nasıl yapılır: XML yükleme bir dosyadan (C#)</span><span class="sxs-lookup"><span data-stu-id="9480e-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="9480e-110">XML kullanarak bir URI yüklemeyi gösterir <xref:System.Xml.Linq.XElement.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9480e-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="9480e-111">XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma</span><span class="sxs-lookup"><span data-stu-id="9480e-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="9480e-112">Boşluk davranışını denetlemek nasıl açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçlarını yüklenirken.</span><span class="sxs-lookup"><span data-stu-id="9480e-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="9480e-113">Nasıl yapılır: ayrıştırma (C#) hatalarını yakalama</span><span class="sxs-lookup"><span data-stu-id="9480e-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="9480e-114">Hatalı biçimlendirilmiş veya geçersiz XML nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="9480e-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="9480e-115">Nasıl yapılır: Xmlreader'dan (C#) bir ağaç oluşturun</span><span class="sxs-lookup"><span data-stu-id="9480e-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="9480e-116">Bir XML ağacı doğrudan nasıl oluşturulacağını gösterir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9480e-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="9480e-117">Nasıl yapılır: Stream parçalarını xmlreader'dan (C#)</span><span class="sxs-lookup"><span data-stu-id="9480e-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="9480e-118">Kullanarak XML parçalarının akışını yapma hakkında gösteren bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9480e-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="9480e-119">Büyük XML dosyalarını işlemek varsa, tüm XML ağacının belleğe yüklemek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9480e-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="9480e-120">Bunun yerine, XML parçalarının akışını yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9480e-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9480e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9480e-121">See Also</span></span>

- [<span data-ttu-id="9480e-122">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="9480e-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
