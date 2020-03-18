---
title: XElement ve XDocument Nesneleringeçerli İçeriği3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590940"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="e7d63-102">XElement ve XDocument Nesnelerinin Geçerli İçeriği</span><span class="sxs-lookup"><span data-stu-id="e7d63-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="e7d63-103">Bu konu, öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebilen geçerli bağımsız değişkenleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7d63-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="e7d63-104">Geçerli İçerik</span><span class="sxs-lookup"><span data-stu-id="e7d63-104">Valid Content</span></span>  
 <span data-ttu-id="e7d63-105">Sorgular <xref:System.Collections.Generic.IEnumerable%601> genellikle <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute>'nin veya</span><span class="sxs-lookup"><span data-stu-id="e7d63-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="e7d63-106">Koleksiyonlarını veya <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> nesnelerini <xref:System.Xml.Linq.XElement> oluşturucuya geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7d63-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="e7d63-107">Bu nedenle, xml ağaçları doldurmak için kullandığınız yöntemler ve yapıcılar içine içerik olarak bir sorgu sonuçlarını geçmek için uygundur.</span><span class="sxs-lookup"><span data-stu-id="e7d63-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="e7d63-108">Basit içerik eklerken, bu yönteme çeşitli türler de aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="e7d63-109">Geçerli türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e7d63-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="e7d63-110">Uygulayan herhangi bir `Object.ToString`tür.</span><span class="sxs-lookup"><span data-stu-id="e7d63-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="e7d63-111">Uygulayan herhangi bir <xref:System.Collections.Generic.IEnumerable%601>tür.</span><span class="sxs-lookup"><span data-stu-id="e7d63-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="e7d63-112">Karmaşık içerik eklerken, çeşitli türler bu yönteme geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="e7d63-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="e7d63-113">Uygulayan herhangi bir tür<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="e7d63-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="e7d63-114">Bir nesne uygularsa, <xref:System.Collections.Generic.IEnumerable%601>nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="e7d63-115">Koleksiyon <xref:System.Xml.Linq.XNode> içeriyorsa <xref:System.Xml.Linq.XAttribute> veya nesnelere, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="e7d63-116">Koleksiyon metin (veya metne dönüştürülen nesneler) içeriyorsa, koleksiyondaki metin birleştirilmiş ve tek bir metin düğümü olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="e7d63-117">İçerik ise, `null`hiçbir şey eklenmez.</span><span class="sxs-lookup"><span data-stu-id="e7d63-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="e7d63-118">Koleksiyondaki bir koleksiyon öğesi geçerken `null`.</span><span class="sxs-lookup"><span data-stu-id="e7d63-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="e7d63-119">Koleksiyondaki bir `null` öğenin ağaç üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e7d63-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="e7d63-120">Eklenen bir öznitelik, içerdiği öğe içinde benzersiz bir ada sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7d63-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="e7d63-121">Eklerken <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute> veya nesneler eklerken, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="e7d63-122">Yeni içerik zaten ebeveynliyse ve başka bir XML ağacının parçasıysa, yeni içerik klonlanır ve yeni klonlanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="e7d63-123">Belgeler için Geçerli İçerik</span><span class="sxs-lookup"><span data-stu-id="e7d63-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="e7d63-124">Bir belgeye öznitelikler ve basit içerik eklenemez.</span><span class="sxs-lookup"><span data-stu-id="e7d63-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="e7d63-125">Bir <xref:System.Xml.Linq.XDocument>tane oluşturmanızı gerektiren çok fazla senaryo yoktur.</span><span class="sxs-lookup"><span data-stu-id="e7d63-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="e7d63-126">Bunun yerine, genellikle <xref:System.Xml.Linq.XElement> bir kök düğümü ile XML ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7d63-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="e7d63-127">Belge oluşturmak için belirli bir gereksiniminiz yoksa (örneğin, en üst düzeyde işleme yönergeleri ve açıklamaları oluşturmanız veya belge türlerini <xref:System.Xml.Linq.XElement> desteklemeniz gerekmediği için), kök düğümünüz olarak kullanmak genellikle daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="e7d63-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="e7d63-128">Bir belge için geçerli içerik aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e7d63-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="e7d63-129">Sıfır veya <xref:System.Xml.Linq.XDocumentType> bir nesne.</span><span class="sxs-lookup"><span data-stu-id="e7d63-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="e7d63-130">Belge türleri öğeden önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="e7d63-131">Sıfır veya bir öğe.</span><span class="sxs-lookup"><span data-stu-id="e7d63-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="e7d63-132">Sıfır veya daha fazla yorum.</span><span class="sxs-lookup"><span data-stu-id="e7d63-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="e7d63-133">Sıfır veya daha fazla işlem talimatı.</span><span class="sxs-lookup"><span data-stu-id="e7d63-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="e7d63-134">Yalnızca beyaz boşluk içeren sıfır veya daha fazla metin düğümü.</span><span class="sxs-lookup"><span data-stu-id="e7d63-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="e7d63-135">İçerik Eklemeye İzin Veren Yapıcılar ve İşlevler</span><span class="sxs-lookup"><span data-stu-id="e7d63-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="e7d63-136">Aşağıdaki yöntemler, bir veya bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>alt içerik eklemek için izin verir:</span><span class="sxs-lookup"><span data-stu-id="e7d63-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="e7d63-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e7d63-137">Method</span></span>|<span data-ttu-id="e7d63-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7d63-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="e7d63-139">Bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e7d63-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="e7d63-140">Bir <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="e7d63-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="e7d63-141">Or'un alt içeriğinin <xref:System.Xml.Linq.XElement> sonuna <xref:System.Xml.Linq.XDocument>ekler.</span><span class="sxs-lookup"><span data-stu-id="e7d63-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="e7d63-142">Sonra içerik <xref:System.Xml.Linq.XNode>ekler.</span><span class="sxs-lookup"><span data-stu-id="e7d63-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="e7d63-143">Önce içerik <xref:System.Xml.Linq.XNode>ekler.</span><span class="sxs-lookup"><span data-stu-id="e7d63-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="e7d63-144">Alt içeriğin başında içerik <xref:System.Xml.Linq.XContainer>ekler.</span><span class="sxs-lookup"><span data-stu-id="e7d63-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="e7d63-145">Bir <xref:System.Xml.Linq.XElement>'nin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="e7d63-146">Bir <xref:System.Xml.Linq.XElement>' nin özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="e7d63-147">Çocuk düğümlerini yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="e7d63-148">Düğümü yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e7d63-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7d63-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7d63-149">See also</span></span>

- [<span data-ttu-id="e7d63-150">XML Ağaçları Oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="e7d63-150">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
