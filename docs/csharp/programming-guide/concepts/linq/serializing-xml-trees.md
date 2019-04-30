---
title: Serileştirmek XML ağaçları (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: a1c39c4c85cbd01fa7c3f3f99f2dfae49e3721d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711739"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="b5b18-102">Serileştirmek XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="b5b18-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="b5b18-103">Bir XML ağacı seri hale getirme, XML XML ağacından oluşturma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5b18-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="b5b18-104">' In somut bir uygulama için bir dosyaya serileştirmek <xref:System.IO.TextWriter> sınıfı veya somut bir uygulama bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b5b18-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="b5b18-105">Serileştirme çeşitli yönlerini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5b18-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="b5b18-106">Örneğin, girinti serileştirilmiş XML verilip verilmeyeceğini ve bir XML bildirimi yazılıp yazılmayacağını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5b18-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5b18-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b5b18-107">In This Section</span></span>  
  
|<span data-ttu-id="b5b18-108">Konu</span><span class="sxs-lookup"><span data-stu-id="b5b18-108">Topic</span></span>|<span data-ttu-id="b5b18-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5b18-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b5b18-110">Serileştirirken Boşlukları Koruma</span><span class="sxs-lookup"><span data-stu-id="b5b18-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="b5b18-111">XML ağaçlarını serileştirme boşluk davranışını denetlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5b18-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="b5b18-112">(C#) bir XML bildirimi ile serileştirme</span><span class="sxs-lookup"><span data-stu-id="b5b18-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="b5b18-113">Bir XML bildirimi içeren bir XML ağacı seri hale getirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5b18-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="b5b18-114">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b5b18-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="b5b18-115">Belgeyi seri hale getirmek açıklar bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b5b18-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="b5b18-116">(Çağrılıyor XSLT) XmlReader'a serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="b5b18-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="b5b18-117">Nasıl oluşturulacağını açıklar bir <xref:System.Xml.XmlReader> bir XML ağacı içeriğini okumak başka bir modül sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5b18-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5b18-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5b18-118">See also</span></span>

- [<span data-ttu-id="b5b18-119">Programlama Kılavuzu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b5b18-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
