---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 917129a06483ce2001e178d744440504533d28d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369017"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="1bf8b-102">LINQ to XML Ek Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="1bf8b-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="1bf8b-103">İçindeki ek açıklamalar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] BIR XML ağacındaki herhangi BIR XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bf8b-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="1bf8b-104">Bir XML bileşenine bir veya gibi bir ek açıklama eklemek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="1bf8b-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="1bf8b-105">Ek açıklamaları türe göre alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1bf8b-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="1bf8b-106">Ek açıklamaların XML bilgi kümesinin bir parçası olmadığına unutmayın; Bunlar serileştirilmez veya seri durumdan çıkarılmaz.</span><span class="sxs-lookup"><span data-stu-id="1bf8b-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1bf8b-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1bf8b-107">Methods</span></span>  
 <span data-ttu-id="1bf8b-108">Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1bf8b-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="1bf8b-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1bf8b-109">Method</span></span>|<span data-ttu-id="1bf8b-110">Description</span><span class="sxs-lookup"><span data-stu-id="1bf8b-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="1bf8b-111">Ek açıklama listesine bir nesne ekler <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="1bf8b-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="1bf8b-112">Belirtilen türdeki ilk ek açıklama nesnesini bir kaynağından alır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="1bf8b-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="1bf8b-113">İçin belirtilen türde ek açıklamaların bir koleksiyonunu alır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="1bf8b-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="1bf8b-114">Belirtilen türdeki ek açıklamaları bir öğesinden kaldırır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="1bf8b-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bf8b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf8b-115">See also</span></span>

- [<span data-ttu-id="1bf8b-116">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bf8b-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
