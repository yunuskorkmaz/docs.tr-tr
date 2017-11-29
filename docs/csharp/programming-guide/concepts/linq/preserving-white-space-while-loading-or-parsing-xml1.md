---
title: "Beyaz alan yüklenirken veya XML1 Ayrıştırma sırasında koruma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bc4923ef5ea526de3c988636cd766c3b012c902e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="cfa21-102">Beyaz alan yüklenirken veya XML Ayrıştırma sırasında koruma</span><span class="sxs-lookup"><span data-stu-id="cfa21-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="cfa21-103">Bu konu, boşluk davranışını denetlemek açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cfa21-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="cfa21-104">Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="cfa21-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="cfa21-105">Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="cfa21-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="cfa21-106">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cfa21-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="cfa21-107">Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="cfa21-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="cfa21-108">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfa21-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="cfa21-109">Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme zaman biçimlendirme devre dışı olduğunda boşluk korumak.</span><span class="sxs-lookup"><span data-stu-id="cfa21-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="cfa21-110">Bu konuda XML ağaçları doldurmak yöntemleri boşluk davranışını açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cfa21-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="cfa21-111">XML ağaçları seri boşluk denetleme hakkında daha fazla bilgi için bkz: [koruma boşluk sırada seri hale getirme](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="cfa21-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="cfa21-112">XML ağaçları doldurmak yöntemleri davranışı</span><span class="sxs-lookup"><span data-stu-id="cfa21-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="cfa21-113">Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları doldurmak bir XML ağacı.</span><span class="sxs-lookup"><span data-stu-id="cfa21-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="cfa21-114">Bir dosyayı bir XML ağacından doldurabilirsiniz bir <xref:System.IO.TextReader>, bir <xref:System.Xml.XmlReader>, veya bir dize:</span><span class="sxs-lookup"><span data-stu-id="cfa21-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="cfa21-115">Yöntem değil izlerseniz <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak Önemsiz boşluk yöntemi korumaz.</span><span class="sxs-lookup"><span data-stu-id="cfa21-115">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="cfa21-116">Çoğu durumda, yöntem sürerse <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak, isteğe bağlı olarak Önemsiz boşluk XML ağacında metin düğümleri olarak koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfa21-116">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="cfa21-117">Ancak, XML'den yöntemi yüklenirken, bir <xref:System.Xml.XmlReader>, sonra <xref:System.Xml.XmlReader> boşluk veya korunması olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="cfa21-117">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="cfa21-118">Ayarı <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="cfa21-118">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>  
  
 <span data-ttu-id="cfa21-119">Beyaz alan korunuyorsa, bu yöntemlerle anlamsız boşluk XML ağaç olarak eklenir <xref:System.Xml.Linq.XText> düğümleri.</span><span class="sxs-lookup"><span data-stu-id="cfa21-119">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="cfa21-120">Beyaz alan korunmaz, metin düğümleri eklenmez.</span><span class="sxs-lookup"><span data-stu-id="cfa21-120">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="cfa21-121">Bir XML ağacı kullanarak oluşturabileceğiniz bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="cfa21-121">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="cfa21-122">Yazılan düğümleri <xref:System.Xml.XmlWriter> ağacında doldurulur.</span><span class="sxs-lookup"><span data-stu-id="cfa21-122">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="cfa21-123">Bu yöntemi kullanarak bir XML ağacı yapılandırdığınızda, Bununla birlikte, tüm düğümler korunan, düğüm boşluk olup ya da boşluk önemli olup olmamasına bakılmaksızın.</span><span class="sxs-lookup"><span data-stu-id="cfa21-123">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa21-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa21-124">See Also</span></span>  
 [<span data-ttu-id="cfa21-125">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="cfa21-125">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
