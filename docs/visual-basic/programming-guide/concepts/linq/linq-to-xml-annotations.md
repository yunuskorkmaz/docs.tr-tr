---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: edf8e0126c632deae6b6d4c235c4880d7b8687e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831757"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="1a62b-102">LINQ to XML Ek Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="1a62b-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="1a62b-103">Ek açıklamalarda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rasgele türden herhangi bir rastgele nesne XML ağacındaki herhangi bir XML bileşeni ile ilişkilendirilecek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a62b-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="1a62b-104">Ek açıklamanın gibi bir XML bileşenine eklemek için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>, çağırmanızı <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a62b-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="1a62b-105">Türe göre ek açıklamaları aldığınız.</span><span class="sxs-lookup"><span data-stu-id="1a62b-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="1a62b-106">Ek açıklamaları XML bilgi kümesi parçası olmadığını unutmayın; Kullanıcılar seri durumdan veya.</span><span class="sxs-lookup"><span data-stu-id="1a62b-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a62b-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1a62b-107">Methods</span></span>  
 <span data-ttu-id="1a62b-108">Ek açıklamalar ile çalışırken aşağıdaki yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a62b-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="1a62b-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1a62b-109">Method</span></span>|<span data-ttu-id="1a62b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a62b-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="1a62b-111">Bir nesne ekler, ek açıklama listesine bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1a62b-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="1a62b-112">Belirtilen türden ilk ek açıklama nesnesinin alır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1a62b-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="1a62b-113">Ek açıklamalar için belirtilen türün bir koleksiyonunu alır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1a62b-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="1a62b-114">Ek açıklamalar, belirtilen türden kaldırır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1a62b-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a62b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a62b-115">See also</span></span>

- [<span data-ttu-id="1a62b-116">Gelişmiş LINQ to XML programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a62b-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
