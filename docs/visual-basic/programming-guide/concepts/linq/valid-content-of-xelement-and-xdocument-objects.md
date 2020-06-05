---
title: XElement ve XDocument Objects2 'ın geçerli Içeriği
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: d222f19f6f588968a3ef1515dca522a4a80e1ffb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364350"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="fef70-102">XElement ve XDocument Nesnelerinin Geçerli İçeriği</span><span class="sxs-lookup"><span data-stu-id="fef70-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="fef70-103">Bu konuda, öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebilecek geçerli bağımsız değişkenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fef70-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="fef70-104">Geçerli Içerik</span><span class="sxs-lookup"><span data-stu-id="fef70-104">Valid Content</span></span>  
 <span data-ttu-id="fef70-105">Sorgular genellikle veya ' nin sonucunu vermez <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="fef70-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="fef70-106"><xref:System.Xml.Linq.XElement>Veya <xref:System.Xml.Linq.XAttribute> nesne koleksiyonlarını oluşturucuya geçirebilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fef70-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="fef70-107">Bu nedenle, bir sorgunun sonuçlarını, XML ağaçlarını doldurmak için kullandığınız yöntemlere ve oluşturuculara içerik olarak geçirmek kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="fef70-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="fef70-108">Basit içerik eklerken bu yönteme çeşitli türler geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fef70-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="fef70-109">Geçerli türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fef70-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="fef70-110">Uygulayan herhangi bir tür `Object.ToString` .</span><span class="sxs-lookup"><span data-stu-id="fef70-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="fef70-111">Uygulayan herhangi bir tür <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="fef70-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="fef70-112">Karmaşık içerik eklerken bu yönteme çeşitli türler geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="fef70-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="fef70-113">Uygulayan herhangi bir tür<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="fef70-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="fef70-114">Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="fef70-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="fef70-115">Koleksiyon <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir.</span><span class="sxs-lookup"><span data-stu-id="fef70-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="fef70-116">Koleksiyon metin içeriyorsa (veya metne dönüştürülen nesneler), koleksiyondaki metin birleştirilir ve tek bir metin düğümü olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="fef70-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="fef70-117">İçerik varsa `null` , hiçbir şey eklenmez.</span><span class="sxs-lookup"><span data-stu-id="fef70-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="fef70-118">Koleksiyonda bir koleksiyon öğelerini geçirirken olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="fef70-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="fef70-119">`null`Koleksiyondaki bir öğenin ağacı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fef70-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="fef70-120">Eklenen bir öznitelik, kapsayan öğesi içinde benzersiz bir ada sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fef70-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="fef70-121"><xref:System.Xml.Linq.XNode>Veya nesneleri eklerken <xref:System.Xml.Linq.XAttribute> , yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="fef70-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="fef70-122">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="fef70-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="fef70-123">Belgeler için geçerli Içerik</span><span class="sxs-lookup"><span data-stu-id="fef70-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="fef70-124">Öznitelikler ve basit içerik belgeye eklenemez.</span><span class="sxs-lookup"><span data-stu-id="fef70-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="fef70-125">Oluşturmanız gereken pek çok senaryo yoktur <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="fef70-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="fef70-126">Bunun yerine, genellikle bir kök düğümü olan XML ağaçlarınızı oluşturabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fef70-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="fef70-127">Bir belge oluşturmak için özel bir gereksinime sahip değilseniz (örneğin, en üst düzeyde işlem yönergeleri ve açıklamalar oluşturmanız veya belge türlerini desteklemeniz gerektiğinden), genellikle <xref:System.Xml.Linq.XElement> kök düğümünüz olarak kullanılması daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="fef70-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="fef70-128">Bir belge için geçerli içerik şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="fef70-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="fef70-129">Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesne.</span><span class="sxs-lookup"><span data-stu-id="fef70-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="fef70-130">Belge türlerinin öğeden önce gelmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fef70-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="fef70-131">Sıfır veya bir öğe.</span><span class="sxs-lookup"><span data-stu-id="fef70-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="fef70-132">Sıfır veya daha fazla açıklama.</span><span class="sxs-lookup"><span data-stu-id="fef70-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="fef70-133">Sıfır veya daha fazla işleme yönergesi.</span><span class="sxs-lookup"><span data-stu-id="fef70-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="fef70-134">Yalnızca boşluk içeren sıfır veya daha fazla metin düğümü.</span><span class="sxs-lookup"><span data-stu-id="fef70-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="fef70-135">Içerik eklemeye Izin veren oluşturucular ve Işlevler</span><span class="sxs-lookup"><span data-stu-id="fef70-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="fef70-136">Aşağıdaki yöntemler bir veya öğesine alt içerik eklemenize olanak tanır <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="fef70-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="fef70-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fef70-137">Method</span></span>|<span data-ttu-id="fef70-138">Description</span><span class="sxs-lookup"><span data-stu-id="fef70-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="fef70-139">Oluşturur <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fef70-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="fef70-140">Bir oluşturur <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="fef70-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="fef70-141">Veya alt içeriğinin sonuna ekler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="fef70-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="fef70-142">Öğesinden sonra içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="fef70-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="fef70-143">Öğesinden önce içerik ekler <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="fef70-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="fef70-144">Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="fef70-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="fef70-145">Bir öğesinin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fef70-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="fef70-146">İçindeki özniteliklerini değiştirir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fef70-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="fef70-147">Alt düğümleri yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fef70-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="fef70-148">Bir düğümü yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fef70-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fef70-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fef70-149">See also</span></span>

- [<span data-ttu-id="fef70-150">XML ağaçları oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fef70-150">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
