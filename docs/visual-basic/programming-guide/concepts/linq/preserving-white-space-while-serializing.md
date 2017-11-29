---
title: "While Serializing2 boşluk koruma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 93cfc1c14d75078170d6e1bbb3fc4ad72f47a206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="b9b76-102">Beyaz alan Serileştirirken koruma</span><span class="sxs-lookup"><span data-stu-id="b9b76-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="b9b76-103">Bu konuda, bir XML ağacı serileştirilirken boşluk denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9b76-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="b9b76-104">Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="b9b76-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="b9b76-105">Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="b9b76-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="b9b76-106">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9b76-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="b9b76-107">Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="b9b76-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="b9b76-108">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9b76-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="b9b76-109">Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme zaman biçimlendirme devre dışı olduğunda boşluk korumak.</span><span class="sxs-lookup"><span data-stu-id="b9b76-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="b9b76-110">Beyaz alan davranışı XML ağaçları Serialize yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9b76-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="b9b76-111">Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları seri bir XML ağacı.</span><span class="sxs-lookup"><span data-stu-id="b9b76-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="b9b76-112">Bir dosyayı bir XML ağaca serileştirebiliyorsa bir <xref:System.IO.TextReader>, veya bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b9b76-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b9b76-113">`ToString` Yöntemi serileştiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b9b76-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="b9b76-114">Yöntem değil izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirir (Girinti) serileştirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="b9b76-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="b9b76-115">Bu durumda, tüm anlamsız boşluk XML ağacında göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="b9b76-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="b9b76-116">Yöntem izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirme olduğunu belirleyebilirsiniz (Girinti) serileştirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="b9b76-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="b9b76-117">Bu durumda, tüm boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="b9b76-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b76-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9b76-118">See Also</span></span>  
 [<span data-ttu-id="b9b76-119">Biçimlendiricisi XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9b76-119">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
