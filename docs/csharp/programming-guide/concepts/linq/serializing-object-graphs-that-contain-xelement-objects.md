---
title: "XElement nesneler (C#) içeren nesne grafiklerinin seri hale getirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b7da4429360beb20fa304b592020d48666fe732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="242ae-102">XElement nesneler (C#) içeren nesne grafiklerinin seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="242ae-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="242ae-103">Bu konu, başvuru türünde nesneler içeren nesne grafiklerinin seri hale getirme yeteneği tanıtır <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="242ae-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="242ae-104">Tesis için seri hale getirme, bu tür <xref:System.Xml.Linq.XElement> uygulayan <xref:System.Xml.Serialization.IXmlSerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="242ae-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="242ae-105">Yalnızca Not <xref:System.Xml.Linq.XElement> sınıfı serileştirme uygular.</span><span class="sxs-lookup"><span data-stu-id="242ae-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="242ae-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="242ae-106">In This Section</span></span>  
  
|<span data-ttu-id="242ae-107">Konu</span><span class="sxs-lookup"><span data-stu-id="242ae-107">Topic</span></span>|<span data-ttu-id="242ae-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="242ae-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="242ae-109">Nasıl yapılır: XmlSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="242ae-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="242ae-110">Kullanarak serileştirmek gösterilmiştir <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="242ae-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="242ae-111">Nasıl yapılır: DataContractSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="242ae-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="242ae-112">Kullanarak serileştirmek gösterilmiştir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="242ae-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="242ae-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="242ae-113">See Also</span></span>  
 [<span data-ttu-id="242ae-114">Gelişmiş LINQ-XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="242ae-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
