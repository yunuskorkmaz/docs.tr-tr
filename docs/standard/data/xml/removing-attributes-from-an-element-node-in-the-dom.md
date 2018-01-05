---
title: "DOM öğesi düğümünde öznitelikleri kaldırılıyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 967344db880347bde94330912bc5689c57b29921
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="28f47-102">DOM öğesi düğümünde öznitelikleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="28f47-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="28f47-103">Öznitelikleri kaldırmak için birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="28f47-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="28f47-104">Bir öznitelik Koleksiyondan kaldırılacak tekniktir.</span><span class="sxs-lookup"><span data-stu-id="28f47-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="28f47-105">Bunu yapmak için aşağıdaki adımlar gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="28f47-105">To do this, the following steps are performed:</span></span>  
  
1.  <span data-ttu-id="28f47-106">Öznitelik koleksiyonu öğesi kullanımından almak `XmlAttributeCollection attrs = elem.Attributes;`.</span><span class="sxs-lookup"><span data-stu-id="28f47-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2.  <span data-ttu-id="28f47-107">Öznitelik üç yöntemden birini kullanarak özniteliği koleksiyondan kaldırın:</span><span class="sxs-lookup"><span data-stu-id="28f47-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="28f47-108">Kullanım <xref:System.Xml.XmlAttributeCollection.Remove%2A> belirli bir özniteliği kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="28f47-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="28f47-109">Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> tüm öznitelikleri koleksiyondan kaldırmak ve özniteliklere öğe bırakın.</span><span class="sxs-lookup"><span data-stu-id="28f47-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="28f47-110">Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> dizin numarasını kullanarak bir özniteliği öznitelik Koleksiyondan kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="28f47-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="28f47-111">Aşağıdaki yöntemlerden öznitelikleri öğesi düğümünden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="28f47-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="28f47-112">Kullanım <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> öznitelik koleksiyonu kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="28f47-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="28f47-113">Kullanım <xref:System.Xml.XmlElement.RemoveAttribute%2A> adıyla tek bir öznitelik Koleksiyondan kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="28f47-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="28f47-114">Kullanım <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> tek bir öznitelik tarafından dizin numarasını Koleksiyondan kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="28f47-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="28f47-115">Bir daha fazla öğe almak, öznitelik öznitelik koleksiyonundan almak ve öznitelik düğümü doğrudan kaldırmak için alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="28f47-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="28f47-116">Öznitelik öznitelik koleksiyonundan almak için bir ad kullanabilirsiniz `XmlAttribute attr = attrs["attr_name"];`, bir dizin `XmlAttribute attr = attrs[0];`, veya ad alanı adıyla tam olarak niteleme `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span><span class="sxs-lookup"><span data-stu-id="28f47-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="28f47-117">Öznitelikleri kaldırmak için kullanılan yöntem bağımsız olarak, varsayılan öznitelikler belge türü tanımı (DTD) olarak tanımlanan öznitelikleri kaldırma özel sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="28f47-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="28f47-118">Ait oldukları öğesi kaldırılmadığı sürece varsayılan öznitelikleri kaldırılamaz.</span><span class="sxs-lookup"><span data-stu-id="28f47-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="28f47-119">Varsayılan öznitelikleri her zaman için bildirilen varsayılan özniteliklere sahip öğeleri yok.</span><span class="sxs-lookup"><span data-stu-id="28f47-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="28f47-120">Bir varsayılan özniteliğinden kaldırma bir <xref:System.Xml.XmlAttributeCollection> veya <xref:System.Xml.XmlElement> değiştirme özniteliği sonuçlarında eklenen içine <xref:System.Xml.XmlAttributeCollection> öğesinin varsayılan değerin bildirildi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="28f47-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="28f47-121">Olarak tanımlanan bir öğe varsa `<book att1="1" att2="2" att3="3"></book>`, sahip olduğunuz sonra bir `book` üç varsayılan özniteliklerle öğesi bildirildi.</span><span class="sxs-lookup"><span data-stu-id="28f47-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="28f47-122">XML belge nesne modeli (DOM) uygulama garanti sürece bu `book` öğesi var, bu üç varsayılan özniteliklerini sahip `att1`, `att2`, ve `att3`.</span><span class="sxs-lookup"><span data-stu-id="28f47-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="28f47-123">İle çağrıldığında bir <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> yöntemi bir özniteliği olmayan bir değer bulunduğundan bu özniteliğin değeri String.Empty için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="28f47-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f47-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28f47-124">See Also</span></span>  
 [<span data-ttu-id="28f47-125">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="28f47-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
