---
title: "Beyaz alan yüklenirken veya XML2 Ayrıştırma sırasında koruma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d99cea37bb9817c40a6d3876b72ccdbd84d7e7ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="fa695-102">Beyaz alan yüklenirken veya XML Ayrıştırma sırasında koruma</span><span class="sxs-lookup"><span data-stu-id="fa695-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="fa695-103">Bu konu, boşluk davranışını denetlemek açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa695-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="fa695-104">Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="fa695-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="fa695-105">Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="fa695-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="fa695-106">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa695-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="fa695-107">Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="fa695-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="fa695-108">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa695-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="fa695-109">Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme zaman biçimlendirme devre dışı olduğunda boşluk korumak.</span><span class="sxs-lookup"><span data-stu-id="fa695-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="fa695-110">Bu konuda XML ağaçları doldurmak yöntemleri boşluk davranışını açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa695-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="fa695-111">XML ağaçları seri boşluk denetleme hakkında daha fazla bilgi için bkz: [koruma boşluk sırada seri hale getirme](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="fa695-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="fa695-112">XML ağaçları doldurmak yöntemleri davranışı</span><span class="sxs-lookup"><span data-stu-id="fa695-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="fa695-113">Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları doldurmak bir XML ağacı.</span><span class="sxs-lookup"><span data-stu-id="fa695-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="fa695-114">Bir dosyayı bir XML ağacından doldurabilirsiniz bir <xref:System.IO.TextReader>, bir <xref:System.Xml.XmlReader>, veya bir dize:</span><span class="sxs-lookup"><span data-stu-id="fa695-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="fa695-115">Yöntem değil izlerseniz <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak Önemsiz boşluk yöntemi korumaz.</span><span class="sxs-lookup"><span data-stu-id="fa695-115">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="fa695-116">Çoğu durumda, yöntem sürerse <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak, isteğe bağlı olarak Önemsiz boşluk XML ağacında metin düğümleri olarak koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa695-116">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="fa695-117">Ancak, XML'den yöntemi yüklenirken, bir <xref:System.Xml.XmlReader>, sonra <xref:System.Xml.XmlReader> boşluk veya korunması olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fa695-117">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="fa695-118">Ayarı <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="fa695-118">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>  
  
 <span data-ttu-id="fa695-119">Beyaz alan korunuyorsa, bu yöntemlerle anlamsız boşluk XML ağaç olarak eklenir <xref:System.Xml.Linq.XText> düğümleri.</span><span class="sxs-lookup"><span data-stu-id="fa695-119">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="fa695-120">Beyaz alan korunmaz, metin düğümleri eklenmez.</span><span class="sxs-lookup"><span data-stu-id="fa695-120">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="fa695-121">Bir XML ağacı kullanarak oluşturabileceğiniz bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="fa695-121">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="fa695-122">Yazılan düğümleri <xref:System.Xml.XmlWriter> ağacında doldurulur.</span><span class="sxs-lookup"><span data-stu-id="fa695-122">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="fa695-123">Bu yöntemi kullanarak bir XML ağacı yapılandırdığınızda, Bununla birlikte, tüm düğümler korunan, düğüm boşluk olup ya da boşluk önemli olup olmamasına bakılmaksızın.</span><span class="sxs-lookup"><span data-stu-id="fa695-123">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa695-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa695-124">See Also</span></span>  
 [<span data-ttu-id="fa695-125">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa695-125">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
