---
title: XML Ağaçlarını Serileştirme
ms.date: 07/20/2015
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
ms.openlocfilehash: 6b91078ff7f1b0410f97be9bc9ed3601f3ca0733
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351044"
---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="8b58e-102">XML ağaçlarını serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b58e-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="8b58e-103">Xml ağacının serileştirilmesi xml ağacının XML oluşturma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8b58e-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="8b58e-104">Bir dosyaya, <xref:System.IO.TextWriter> sınıfının somut bir uygulamasına veya bir <xref:System.Xml.XmlWriter>somut uygulamasına seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b58e-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="8b58e-105">Serileştirme çeşitli yönlerini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b58e-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="8b58e-106">Örneğin, seri hale getirilmiş XML 'in girintisini ve bir XML bildirimi mi yazılacağını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b58e-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b58e-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8b58e-107">In This Section</span></span>  
  
|<span data-ttu-id="8b58e-108">Konu</span><span class="sxs-lookup"><span data-stu-id="8b58e-108">Topic</span></span>|<span data-ttu-id="8b58e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b58e-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8b58e-110">Serileştirirken Boşlukları Koruma</span><span class="sxs-lookup"><span data-stu-id="8b58e-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="8b58e-111">XML ağaçlarını seri hale alırken boşluk davranışının nasıl kontrol edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b58e-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="8b58e-112">XML bildirimiyle serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b58e-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="8b58e-113">XML bildirimi içeren bir XML ağacının serileştirilme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b58e-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="8b58e-114">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8b58e-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="8b58e-115">Bir <xref:System.IO.File>, <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>bir belgenin serileştirilme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b58e-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="8b58e-116">XmlReader 'a serileştirme (XSLT çağırma) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b58e-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="8b58e-117">Başka bir modülün bir XML ağacının içeriğini okumasını sağlayan bir <xref:System.Xml.XmlReader> oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b58e-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b58e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b58e-118">See also</span></span>

- [<span data-ttu-id="8b58e-119">Programlama Kılavuzu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b58e-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
