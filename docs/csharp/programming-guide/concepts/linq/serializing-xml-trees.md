---
title: Biçimlendiricisi XML ağaçları (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: 8f372a05bd69b801085cba9d9a3b11ae01841a2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338357"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="8b7ce-102">Biçimlendiricisi XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="8b7ce-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="8b7ce-103">Bir XML ağacı seri hale getirme XML ağacından XML oluşturma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="8b7ce-104">Bir dosyaya somut bir uyarlamasını serileştirebilen <xref:System.IO.TextWriter> sınıfı veya somut bir uygulaması için bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="8b7ce-105">Seri hale getirme çeşitli yönlerini kontrol edebilir.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="8b7ce-106">Örneğin, serileştirilmiş XML girinti mı yoksa ve bir XML bildirimi yazılıp yazılmayacağını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b7ce-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8b7ce-107">In This Section</span></span>  
  
|<span data-ttu-id="8b7ce-108">Konu</span><span class="sxs-lookup"><span data-stu-id="8b7ce-108">Topic</span></span>|<span data-ttu-id="8b7ce-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b7ce-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8b7ce-110">Serileştirirken Boşlukları Koruma</span><span class="sxs-lookup"><span data-stu-id="8b7ce-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="8b7ce-111">XML ağaçları seri boşluk davranışını denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="8b7ce-112">Seri hale getirilirken bir XML bildirimi ile (C#)</span><span class="sxs-lookup"><span data-stu-id="8b7ce-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="8b7ce-113">Bir XML bildirimi içeren bir XML ağacı serileştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="8b7ce-114">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8b7ce-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="8b7ce-115">Belgeyi seri hale getirmek açıklar bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="8b7ce-116">XmlReader (bildirilecekse XSLT) seri hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="8b7ce-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="8b7ce-117">Nasıl oluşturulacağını açıklar bir <xref:System.Xml.XmlReader> bir XML ağacı içeriğini okumak başka bir modül sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b7ce-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b7ce-118">See Also</span></span>  
 [<span data-ttu-id="8b7ce-119">Programlama Kılavuzu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b7ce-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
