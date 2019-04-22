---
title: (Visual Basic) XML ağaçlarını serileştirme
ms.date: 07/20/2015
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
ms.openlocfilehash: ddcd82a3fe8beea87913227ed0ff86fa3974bd11
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827346"
---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="0cf44-102">(Visual Basic) XML ağaçlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="0cf44-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="0cf44-103">Bir XML ağacı seri hale getirme, XML XML ağacından oluşturma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0cf44-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="0cf44-104">' In somut bir uygulama için bir dosyaya serileştirmek <xref:System.IO.TextWriter> sınıfı veya somut bir uygulama bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="0cf44-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="0cf44-105">Serileştirme çeşitli yönlerini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf44-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="0cf44-106">Örneğin, girinti serileştirilmiş XML verilip verilmeyeceğini ve bir XML bildirimi yazılıp yazılmayacağını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf44-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0cf44-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0cf44-107">In This Section</span></span>  
  
|<span data-ttu-id="0cf44-108">Konu</span><span class="sxs-lookup"><span data-stu-id="0cf44-108">Topic</span></span>|<span data-ttu-id="0cf44-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cf44-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0cf44-110">Serileştirirken Boşlukları Koruma</span><span class="sxs-lookup"><span data-stu-id="0cf44-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="0cf44-111">XML ağaçlarını serileştirme boşluk davranışını denetlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="0cf44-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="0cf44-112">Serileştirmek bir XML bildirimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cf44-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="0cf44-113">Bir XML bildirimi içeren bir XML ağacı seri hale getirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="0cf44-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="0cf44-114">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0cf44-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="0cf44-115">Belgeyi seri hale getirmek açıklar bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="0cf44-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="0cf44-116">(Çağrılıyor XSLT) XmlReader'a serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cf44-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="0cf44-117">Nasıl oluşturulacağını açıklar bir <xref:System.Xml.XmlReader> bir XML ağacı içeriğini okumak başka bir modül sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cf44-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0cf44-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf44-118">See also</span></span>

- [<span data-ttu-id="0cf44-119">Programlama Kılavuzu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cf44-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
