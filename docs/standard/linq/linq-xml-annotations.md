---
title: Ek açıklamalar-LINQ to XML
description: Bir XML ağacındaki herhangi bir XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmek için LINQ to XML ek açıklamaları nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553366"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a><span data-ttu-id="355b4-103">LINQ to XML ek açıklamaları (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="355b4-103">LINQ to XML annotations (LINQ to XML)</span></span>

<span data-ttu-id="355b4-104">LINQ to XML ek açıklamaları bir XML ağacındaki herhangi bir XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="355b4-104">Annotations in LINQ to XML enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="355b4-105">Bir XML bileşenine bir veya gibi bir ek açıklama eklemek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="355b4-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="355b4-106">Ek açıklamaları türe göre alırsınız.</span><span class="sxs-lookup"><span data-stu-id="355b4-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="355b4-107">Ek açıklamaların XML bilgi kümesinin bir parçası olmadığı unutulmamalıdır; Bunlar serileştirilmez veya seri durumdan çıkarılmaz.</span><span class="sxs-lookup"><span data-stu-id="355b4-107">Note that annotations aren't part of the XML infoset; they're not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="355b4-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="355b4-108">Methods</span></span>

<span data-ttu-id="355b4-109">Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="355b4-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="355b4-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="355b4-110">Method</span></span>|<span data-ttu-id="355b4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="355b4-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="355b4-112">Ek açıklama listesine bir nesne ekler <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="355b4-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="355b4-113">Belirtilen türdeki ilk ek açıklama nesnesini bir kaynağından alır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="355b4-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="355b4-114">İçin belirtilen türde ek açıklamaların bir koleksiyonunu alır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="355b4-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="355b4-115">Belirtilen türdeki ek açıklamaları bir öğesinden kaldırır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="355b4-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
