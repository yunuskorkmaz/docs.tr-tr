---
title: Dosyaları, TextWriters ve XmlWriters3 seri hale getirme
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: ff877e3c800bd1409d796fb68d651175d3602e34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645323"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="9daeb-102">Dosyaları, TextWriters ve XmlWriters seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9daeb-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="9daeb-103">XML ağaçları serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9daeb-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="9daeb-104">Herhangi bir XML bileşeni serileştirebilen dahil olmak üzere <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement>, kullanarak bir dizeye `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9daeb-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="9daeb-105">Bir dizeyi serileştirilirken biçimlendirme gizlemek istiyorsanız, kullanabileceğiniz <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9daeb-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9daeb-106">Bir dosyaya serileştirilirken varsayılan (Girinti) sonuç XML belge biçimlendirmek için davranıştır.</span><span class="sxs-lookup"><span data-stu-id="9daeb-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="9daeb-107">Girintisini zaman anlamsız boşluk XML ağacında korunmaz.</span><span class="sxs-lookup"><span data-stu-id="9daeb-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="9daeb-108">Biçimlendirme ile seri hale getirmek için aşırı yararlanabilir mi aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="9daeb-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="9daeb-109">Değil girinti ve önemsiz boşluk XML ağacında korumak için seçeneği istiyorsanız, alan aşırı yüklemeleri aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="9daeb-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="9daeb-110">Örnekler için uygun başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="9daeb-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9daeb-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9daeb-111">See Also</span></span>  
 [<span data-ttu-id="9daeb-112">Biçimlendiricisi XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9daeb-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
