---
title: DOM'da bir öğe düğümünden öznitelikleri kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65fd6d2baae29c72241350e4568faf09b9c71f39
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44136725"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="21402-102">DOM'da bir öğe düğümünden öznitelikleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="21402-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="21402-103">Öznitelikleri kaldırmak için birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="21402-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="21402-104">Öznitelik koleksiyonundan kaldırabilirsiniz bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="21402-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="21402-105">Bunu yapmak için aşağıdaki adımları gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="21402-105">To do this, the following steps are performed:</span></span>  
  
1.  <span data-ttu-id="21402-106">Öğesini kullanarak gelen öznitelik koleksiyonu alma `XmlAttributeCollection attrs = elem.Attributes;`.</span><span class="sxs-lookup"><span data-stu-id="21402-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2.  <span data-ttu-id="21402-107">Öznitelik, öznitelik koleksiyonundan üç yöntemden birini kullanarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="21402-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="21402-108">Kullanım <xref:System.Xml.XmlAttributeCollection.Remove%2A> belirli bir öznitelik kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="21402-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="21402-109">Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> tüm öznitelikler koleksiyondan Kaldır ve özniteliklere bir öğe bırakın.</span><span class="sxs-lookup"><span data-stu-id="21402-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="21402-110">Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> bir özniteliği öznitelik koleksiyonundan dizin numarası kullanarak kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="21402-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="21402-111">Aşağıdaki yöntemlerden öğe düğümünden öznitelikleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="21402-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="21402-112">Kullanım <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> öznitelik koleksiyonundan kaldırılamadı.</span><span class="sxs-lookup"><span data-stu-id="21402-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="21402-113">Kullanım <xref:System.Xml.XmlElement.RemoveAttribute%2A> tek bir öznitelik ada göre Koleksiyondan kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="21402-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="21402-114">Kullanım <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> tek bir öznitelik koleksiyonundan dizin numarası ile kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="21402-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="21402-115">Öğesi, öznitelik koleksiyonundan öznitelik alma ve doğrudan öznitelik düğümü kaldırmak için bir daha fazla seçenek var.</span><span class="sxs-lookup"><span data-stu-id="21402-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="21402-116">Öznitelik öznitelik koleksiyonundan almak için bir ad kullanabilirsiniz `XmlAttribute attr = attrs["attr_name"];`, dizin `XmlAttribute attr = attrs[0];`, veya ad alanı adıyla tam olarak uygun `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span><span class="sxs-lookup"><span data-stu-id="21402-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="21402-117">Öznitelikleri kaldırmak için kullanılan yöntem ne olursa olsun, varsayılan öznitelikler belge türü tanımı (DTD'nin) olarak tanımlanan öznitelikleri kaldırma hakkında özel sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="21402-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="21402-118">Ait oldukları öğesi kaldırılmadığı sürece, varsayılan öznitelikler kaldırılamaz.</span><span class="sxs-lookup"><span data-stu-id="21402-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="21402-119">Her zaman, varsayılan öznitelikler bildirilmiş olan öğeler için varsayılan öznitelikleri yok.</span><span class="sxs-lookup"><span data-stu-id="21402-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="21402-120">Varsayılan özniteliğinden kaldırma bir <xref:System.Xml.XmlAttributeCollection> veya <xref:System.Xml.XmlElement> değiştirme özniteliği sonuçlarında eklenen içine <xref:System.Xml.XmlAttributeCollection> bildirilen varsayılan değeri olarak başlatılan bir öğe.</span><span class="sxs-lookup"><span data-stu-id="21402-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="21402-121">Olarak tanımlanan bir öğe varsa `<book att1="1" att2="2" att3="3"></book>`, sahip olduğunuz sonra bir `book` varsayılan öznitelikler üç öğeyle bildirilir.</span><span class="sxs-lookup"><span data-stu-id="21402-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="21402-122">XML belge nesne modeli (DOM) uygulaması, garanti olduğu sürece bu `book` öğe varsa, bu üç varsayılan özniteliklerini sahip `att1`, `att2`, ve `att3`.</span><span class="sxs-lookup"><span data-stu-id="21402-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="21402-123">İle çağrıldığında bir <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> yöntemi gibi bir öznitelik, bir değer olmadan var olamaz bu özniteliğin değeri String.Empty için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="21402-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21402-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21402-124">See also</span></span>

- [<span data-ttu-id="21402-125">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="21402-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
