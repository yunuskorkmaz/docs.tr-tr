---
title: LinQ - XML Ek Açıklamaları3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66689949"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="f1b2b-102">LINQ to XML Ek Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="f1b2b-102">LINQ to XML Annotations</span></span>

<span data-ttu-id="f1b2b-103">Herhangi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir rasgele türdeki herhangi bir rasgele nesneyi XML ağacındaki herhangi bir XML bileşeniyle ilişkilendirmenize olanak tanıyan ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="f1b2b-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="f1b2b-104">XML bileşenine bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute>ek açıklama eklemek için , <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemi çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="f1b2b-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="f1b2b-105">Ek açıklamaları türüne göre alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f1b2b-105">You retrieve annotations by type.</span></span>

<span data-ttu-id="f1b2b-106">Ek açıklamaların XML bilgi kümesinin bir parçası olmadığını unutmayın; serileştirilmeyecek veya serileştirilmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="f1b2b-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="f1b2b-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f1b2b-107">Methods</span></span>

<span data-ttu-id="f1b2b-108">Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1b2b-108">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="f1b2b-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f1b2b-109">Method</span></span>|<span data-ttu-id="f1b2b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1b2b-110">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="f1b2b-111">Bir <xref:System.Xml.Linq.XObject>' in ek açıklama listesine bir nesne ekler</span><span class="sxs-lookup"><span data-stu-id="f1b2b-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="f1b2b-112">Belirtilen türün ilk ek açıklama nesnesini <xref:System.Xml.Linq.XObject>bir .'den alır</span><span class="sxs-lookup"><span data-stu-id="f1b2b-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="f1b2b-113">Bir <xref:System.Xml.Linq.XObject>. için belirtilen türdeki ek açıklamalar koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="f1b2b-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="f1b2b-114">Belirtilen türdeki ek açıklamaları bir <xref:System.Xml.Linq.XObject>'den kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f1b2b-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
