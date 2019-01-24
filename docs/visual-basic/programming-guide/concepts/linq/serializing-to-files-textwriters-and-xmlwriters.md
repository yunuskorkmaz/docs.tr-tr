---
title: Dosya, TextWriters ve XmlWriters3 seri hale getirme
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: a9908f04e2621da15f065a86feccc5af5cdac96d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658997"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="f1b62-102">Dosya, TextWriters ve XmlWriters serileştirme</span><span class="sxs-lookup"><span data-stu-id="f1b62-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="f1b62-103">XML ağaçlarını serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f1b62-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="f1b62-104">Herhangi bir XML bileşeni serileştirebiliyorsa dahil olmak üzere <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement>, kullanarak bir dizeye `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1b62-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="f1b62-105">Bir dizeye serileştirilirken biçimlendirme gizlemek istiyorsanız, kullanabileceğiniz <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1b62-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f1b62-106">Bir dosyaya serileştirmek kullanırken varsayılan davranış (Girinti) elde edilen XML belgeyi Biçimlendir sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f1b62-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="f1b62-107">Girintisini zaman anlamsız boşluk XML ağacındaki korunmaz.</span><span class="sxs-lookup"><span data-stu-id="f1b62-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="f1b62-108">Biçimlendirme ile seri hale getirmek için aşırı almaz aşağıdaki yöntemlerden birini kullanın: <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="f1b62-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f1b62-109">Seçeneği değil girinti ve XML ağacındaki Önemsiz bölünemez boşluğu koruyacak istiyorsanız, alan aşırı yüklemeler aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="f1b62-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f1b62-110">Örnekler için uygun bir başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="f1b62-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b62-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1b62-111">See also</span></span>
- [<span data-ttu-id="f1b62-112">(Visual Basic) XML ağaçlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="f1b62-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
