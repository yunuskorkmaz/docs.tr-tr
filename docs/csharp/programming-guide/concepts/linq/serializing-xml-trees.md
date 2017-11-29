---
title: "Biçimlendiricisi XML ağaçları (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 27001dbc92afddc35be12b593f5ba082c29af5f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="a8f68-102">Biçimlendiricisi XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="a8f68-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="a8f68-103">Bir XML ağacı seri hale getirme XML ağacından XML oluşturma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a8f68-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="a8f68-104">Bir dosyaya somut bir uyarlamasını serileştirebilen <xref:System.IO.TextWriter> sınıfı veya somut bir uygulaması için bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a8f68-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="a8f68-105">Seri hale getirme çeşitli yönlerini kontrol edebilir.</span><span class="sxs-lookup"><span data-stu-id="a8f68-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="a8f68-106">Örneğin, serileştirilmiş XML girinti mı yoksa ve bir XML bildirimi yazılıp yazılmayacağını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8f68-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8f68-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a8f68-107">In This Section</span></span>  
  
|<span data-ttu-id="a8f68-108">Konu</span><span class="sxs-lookup"><span data-stu-id="a8f68-108">Topic</span></span>|<span data-ttu-id="a8f68-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8f68-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a8f68-110">Beyaz alan Serileştirirken koruma</span><span class="sxs-lookup"><span data-stu-id="a8f68-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="a8f68-111">XML ağaçları seri boşluk davranışını denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="a8f68-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="a8f68-112">Seri hale getirilirken bir XML bildirimi ile (C#)</span><span class="sxs-lookup"><span data-stu-id="a8f68-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="a8f68-113">Bir XML bildirimi içeren bir XML ağacı serileştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="a8f68-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="a8f68-114">Dosyaları, TextWriters ve XmlWriters seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="a8f68-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="a8f68-115">Belgeyi seri hale getirmek açıklar bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a8f68-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="a8f68-116">XmlReader (bildirilecekse XSLT) seri hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="a8f68-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="a8f68-117">Nasıl oluşturulacağını açıklar bir <xref:System.Xml.XmlReader> bir XML ağacı içeriğini okumak başka bir modül sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8f68-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8f68-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8f68-118">See Also</span></span>  
 [<span data-ttu-id="a8f68-119">Programlama Kılavuzu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a8f68-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
