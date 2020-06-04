---
title: XML Ayrıştırma
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: 3517a0925e886dcd3d2d7860be606c4e44127cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406865"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="3da2a-102">XML 'yi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da2a-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="3da2a-103">Bu bölümdeki konular XML belgelerinin nasıl ayrıştıralınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="3da2a-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3da2a-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3da2a-104">In This Section</span></span>  
  
|<span data-ttu-id="3da2a-105">Konu başlığı</span><span class="sxs-lookup"><span data-stu-id="3da2a-105">Topic</span></span>|<span data-ttu-id="3da2a-106">Description</span><span class="sxs-lookup"><span data-stu-id="3da2a-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3da2a-107">Nasıl yapılır: bir dizeyi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da2a-107">How to: Parse a String (Visual Basic)</span></span>](how-to-parse-a-string.md)|<span data-ttu-id="3da2a-108">Bir XML ağacı oluşturmak için bir dizenin nasıl ayrıştıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da2a-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="3da2a-109">Nasıl yapılır: dosyadan XML yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da2a-109">How to: Load XML from a File (Visual Basic)</span></span>](how-to-load-xml-from-a-file.md)|<span data-ttu-id="3da2a-110">Yöntemi kullanılarak bir URI 'den XML 'nin nasıl yükleneceğini gösterir <xref:System.Xml.Linq.XElement.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="3da2a-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="3da2a-111">XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma</span><span class="sxs-lookup"><span data-stu-id="3da2a-111">Preserving White Space while Loading or Parsing XML</span></span>](preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="3da2a-112">XML ağaçları yüklenirken beyaz boşluk davranışının nasıl kontrol edileceğini açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3da2a-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="3da2a-113">Nasıl yapılır: ayrıştırma hatalarını yakalama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da2a-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](how-to-catch-parsing-errors.md)|<span data-ttu-id="3da2a-114">Hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da2a-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="3da2a-115">Nasıl yapılır: XmlReader 'dan ağaç oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da2a-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="3da2a-116">Doğrudan bir XML ağacının nasıl oluşturulacağını gösterir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="3da2a-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="3da2a-117">Nasıl yapılır: bir XmlReader 'dan XML parçalarını akışa alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da2a-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="3da2a-118">Kullanılarak XML parçalarının nasıl akışının nasıl yapılacağını gösterir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="3da2a-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="3da2a-119">Rastgele büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3da2a-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="3da2a-120">Bunun yerine, XML parçalarını akışla aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3da2a-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3da2a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3da2a-121">See also</span></span>

- [<span data-ttu-id="3da2a-122">XML ağaçları oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da2a-122">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
