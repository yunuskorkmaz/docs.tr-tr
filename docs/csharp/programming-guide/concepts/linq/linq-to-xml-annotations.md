---
title: LINQ to XML Ek Açıklamaları
description: Bir XML ağacındaki herhangi bir XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmek için LINQ to XML ek açıklamaları nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165571"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="4799a-103">LINQ to XML Ek Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="4799a-103">LINQ to XML Annotations</span></span>

<span data-ttu-id="4799a-104">İçindeki ek açıklamalar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] BIR XML ağacındaki herhangi BIR XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4799a-104">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="4799a-105">Bir XML bileşenine bir veya gibi bir ek açıklama eklemek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4799a-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="4799a-106">Ek açıklamaları türe göre alırsınız.</span><span class="sxs-lookup"><span data-stu-id="4799a-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="4799a-107">Ek açıklamaların XML bilgi kümesinin bir parçası olmadığına unutmayın; Bunlar serileştirilmez veya seri durumdan çıkarılmaz.</span><span class="sxs-lookup"><span data-stu-id="4799a-107">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="4799a-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4799a-108">Methods</span></span>

<span data-ttu-id="4799a-109">Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4799a-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="4799a-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4799a-110">Method</span></span>|<span data-ttu-id="4799a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4799a-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="4799a-112">Ek açıklama listesine bir nesne ekler <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="4799a-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="4799a-113">Belirtilen türdeki ilk ek açıklama nesnesini bir kaynağından alır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="4799a-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="4799a-114">İçin belirtilen türde ek açıklamaların bir koleksiyonunu alır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="4799a-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="4799a-115">Belirtilen türdeki ek açıklamaları bir öğesinden kaldırır <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="4799a-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
