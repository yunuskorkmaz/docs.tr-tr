---
title: LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 19661f303ccea411ff6088005cb0198b50781d37
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487396"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="c000d-102">LINQ to XML Ek Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="c000d-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="c000d-103">Ek açıklamalarda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rasgele türden herhangi bir rastgele nesne XML ağacındaki herhangi bir XML bileşeni ile ilişkilendirilecek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c000d-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="c000d-104">Ek açıklamanın gibi bir XML bileşenine eklemek için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>, çağırmanızı <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c000d-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="c000d-105">Türe göre ek açıklamaları aldığınız.</span><span class="sxs-lookup"><span data-stu-id="c000d-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="c000d-106">Ek açıklamaları XML bilgi kümesi parçası olmadığını unutmayın; Kullanıcılar seri durumdan veya.</span><span class="sxs-lookup"><span data-stu-id="c000d-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c000d-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c000d-107">Methods</span></span>  
 <span data-ttu-id="c000d-108">Ek açıklamalar ile çalışırken aşağıdaki yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c000d-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="c000d-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c000d-109">Method</span></span>|<span data-ttu-id="c000d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c000d-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="c000d-111">Bir nesne ekler, ek açıklama listesine bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="c000d-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="c000d-112">Belirtilen türden ilk ek açıklama nesnesinin alır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="c000d-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="c000d-113">Ek açıklamalar için belirtilen türün bir koleksiyonunu alır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="c000d-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="c000d-114">Ek açıklamalar, belirtilen türden kaldırır bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="c000d-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
