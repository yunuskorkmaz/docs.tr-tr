---
title: XElement ve XDocument Objects3 'ın geçerli Içeriği
description: Öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebileceğiniz geçerli bağımsız değişkenler hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302262"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="344f1-103">XElement ve XDocument Nesnelerinin Geçerli İçeriği</span><span class="sxs-lookup"><span data-stu-id="344f1-103">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="344f1-104">Bu konuda, öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebilecek geçerli bağımsız değişkenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="344f1-104">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="344f1-105">Geçerli Içerik</span><span class="sxs-lookup"><span data-stu-id="344f1-105">Valid Content</span></span>  
 <span data-ttu-id="344f1-106">Sorgular genellikle veya ' nin sonucunu vermez <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="344f1-106">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="344f1-107"><xref:System.Xml.Linq.XElement>Veya <xref:System.Xml.Linq.XAttribute> nesne koleksiyonlarını oluşturucuya geçirebilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="344f1-107">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="344f1-108">Bu nedenle, bir sorgunun sonuçlarını, XML ağaçlarını doldurmak için kullandığınız yöntemlere ve oluşturuculara içerik olarak geçirmek kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="344f1-108">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="344f1-109">Basit içerik eklerken bu yönteme çeşitli türler geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="344f1-109">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="344f1-110">Geçerli türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="344f1-110">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="344f1-111">Uygulayan herhangi bir tür `Object.ToString` .</span><span class="sxs-lookup"><span data-stu-id="344f1-111">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="344f1-112">Uygulayan herhangi bir tür <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="344f1-112">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="344f1-113">Karmaşık içerik eklerken bu yönteme çeşitli türler geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="344f1-113">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="344f1-114">Uygulayan herhangi bir tür<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="344f1-114">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="344f1-115">Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="344f1-115">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="344f1-116">Koleksiyon <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir.</span><span class="sxs-lookup"><span data-stu-id="344f1-116">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="344f1-117">Koleksiyon metin içeriyorsa (veya metne dönüştürülen nesneler), koleksiyondaki metin birleştirilir ve tek bir metin düğümü olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="344f1-117">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="344f1-118">İçerik varsa `null` , hiçbir şey eklenmez.</span><span class="sxs-lookup"><span data-stu-id="344f1-118">If content is `null`, nothing is added.</span></span> <span data-ttu-id="344f1-119">Koleksiyonda bir koleksiyon öğelerini geçirirken olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="344f1-119">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="344f1-120">`null`Koleksiyondaki bir öğenin ağacı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="344f1-120">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="344f1-121">Eklenen bir öznitelik, kapsayan öğesi içinde benzersiz bir ada sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="344f1-121">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="344f1-122"><xref:System.Xml.Linq.XNode>Veya nesneleri eklerken <xref:System.Xml.Linq.XAttribute> , yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="344f1-122">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="344f1-123">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="344f1-123">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="344f1-124">Belgeler için geçerli Içerik</span><span class="sxs-lookup"><span data-stu-id="344f1-124">Valid Content for Documents</span></span>  
 <span data-ttu-id="344f1-125">Öznitelikler ve basit içerik belgeye eklenemez.</span><span class="sxs-lookup"><span data-stu-id="344f1-125">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="344f1-126">Oluşturmanız gereken pek çok senaryo yoktur <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="344f1-126">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="344f1-127">Bunun yerine, genellikle bir kök düğümü olan XML ağaçlarınızı oluşturabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="344f1-127">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="344f1-128">Bir belge oluşturmak için özel bir gereksinime sahip değilseniz (örneğin, en üst düzeyde işlem yönergeleri ve açıklamalar oluşturmanız veya belge türlerini desteklemeniz gerektiğinden), genellikle <xref:System.Xml.Linq.XElement> kök düğümünüz olarak kullanılması daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="344f1-128">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="344f1-129">Bir belge için geçerli içerik şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="344f1-129">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="344f1-130">Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesne.</span><span class="sxs-lookup"><span data-stu-id="344f1-130">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="344f1-131">Belge türlerinin öğeden önce gelmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="344f1-131">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="344f1-132">Sıfır veya bir öğe.</span><span class="sxs-lookup"><span data-stu-id="344f1-132">Zero or one element.</span></span>  
  
- <span data-ttu-id="344f1-133">Sıfır veya daha fazla açıklama.</span><span class="sxs-lookup"><span data-stu-id="344f1-133">Zero or more comments.</span></span>  
  
- <span data-ttu-id="344f1-134">Sıfır veya daha fazla işleme yönergesi.</span><span class="sxs-lookup"><span data-stu-id="344f1-134">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="344f1-135">Yalnızca boşluk içeren sıfır veya daha fazla metin düğümü.</span><span class="sxs-lookup"><span data-stu-id="344f1-135">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="344f1-136">Içerik eklemeye Izin veren oluşturucular ve Işlevler</span><span class="sxs-lookup"><span data-stu-id="344f1-136">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="344f1-137">Aşağıdaki yöntemler bir veya öğesine alt içerik eklemenize olanak tanır <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="344f1-137">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="344f1-138">Yöntem</span><span class="sxs-lookup"><span data-stu-id="344f1-138">Method</span></span>|<span data-ttu-id="344f1-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="344f1-139">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="344f1-140">Oluşturur <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="344f1-140">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="344f1-141">Bir oluşturur <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="344f1-141">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="344f1-142">Veya alt içeriğinin sonuna ekler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="344f1-142">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="344f1-143">Öğesinden sonra içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="344f1-143">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="344f1-144">Öğesinden önce içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="344f1-144">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="344f1-145">Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="344f1-145">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="344f1-146">Bir öğesinin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="344f1-146">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="344f1-147">İçindeki özniteliklerini değiştirir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="344f1-147">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="344f1-148">Alt düğümleri yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="344f1-148">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="344f1-149">Bir düğümü yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="344f1-149">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="344f1-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="344f1-150">See also</span></span>

- [<span data-ttu-id="344f1-151">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="344f1-151">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
