---
title: LINQ-XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: a7b81b8c1856c11cb0c5e777f31986a330cf115f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644803"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="e6aa6-102">LINQ-XML ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="e6aa6-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="e6aa6-103">Ek açıklamalar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] herhangi bir rastgele nesne rasgele herhangi bir türde bir XML ağacındaki herhangi bir XML bileşeni ilişkilendirmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="e6aa6-104">Ek açıklamanın bir XML bileşene gibi eklemek için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>, çağırmanız <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="e6aa6-105">Türe göre ek açıklamalarını alır.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="e6aa6-106">Ek Açıklamalar XML bilgi parçası olmadığını unutmayın; Bunlar seri durumdan veya güncelleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6aa6-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e6aa6-107">Methods</span></span>  
 <span data-ttu-id="e6aa6-108">Ek açıklamalar ile çalışırken aşağıdaki yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6aa6-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="e6aa6-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e6aa6-109">Method</span></span>|<span data-ttu-id="e6aa6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6aa6-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="e6aa6-111">Ek açıklama listesine bir nesne ekler bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="e6aa6-112">Belirtilen türden ilk ek açıklama nesnesinin alır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="e6aa6-113">Belirtilen tür için ek açıklamalar koleksiyonunu alır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="e6aa6-114">Belirtilen türden ek açıklamalar kaldırır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6aa6-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6aa6-115">See Also</span></span>  
 [<span data-ttu-id="e6aa6-116">Gelişmiş LINQ-XML programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6aa6-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
