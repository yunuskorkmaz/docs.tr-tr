---
title: XElement ve XDocument Objects3 geçerli içerik
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: afaeed7ba49891380982ec9c3cade43574ab8c16
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732293"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="bb2d7-102">XElement ve XDocument nesnelerinin geçerli içeriği</span><span class="sxs-lookup"><span data-stu-id="bb2d7-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="bb2d7-103">Bu konuda, Oluşturucular ve öğelerini ve belgeleri için içerik eklemek için kullandığınız yöntemlere geçirilen geçerli bağımsız değişkenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="bb2d7-104">Geçerli içeriği</span><span class="sxs-lookup"><span data-stu-id="bb2d7-104">Valid Content</span></span>  
 <span data-ttu-id="bb2d7-105">Sorgular genellikle değerlendirmek için <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="bb2d7-106">Koleksiyonları geçirebilirsiniz <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri için <xref:System.Xml.Linq.XElement> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="bb2d7-107">Bu nedenle, yöntemleri ve XML ağaçlarını doldurmak için kullandığınız oluşturucular bir sorgunun sonuçlarını içeriği olarak geçirmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="bb2d7-108">Basit içerik eklerken, çeşitli türleri bu yönteme geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="bb2d7-109">Geçerli türleri aşağıdakileri kapsamaktadır:</span><span class="sxs-lookup"><span data-stu-id="bb2d7-109">Valid types include the following:</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   <span data-ttu-id="bb2d7-110">Uygulayan herhangi bir tür `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-110">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="bb2d7-111">Uygulayan herhangi bir tür <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="bb2d7-112">Karmaşık içerik eklerken, çeşitli türleri bu yönteme geçirilen:</span><span class="sxs-lookup"><span data-stu-id="bb2d7-112">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   <span data-ttu-id="bb2d7-113">Uygulayan herhangi bir tür <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="bb2d7-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="bb2d7-114">Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, koleksiyon nesnesi içinde listelenmiş ve koleksiyondaki tüm öğelerin eklenir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="bb2d7-115">Koleksiyon içeriyorsa <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="bb2d7-116">Koleksiyon, metin (veya metne dönüştürülür nesneleri) içeriyorsa, koleksiyondaki metin birleştirilmiş ve tek bir metin düğümü olarak eklendi.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="bb2d7-117">İçerik `null`, hiçbir şey eklenir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="bb2d7-118">Ne zaman bir koleksiyon, koleksiyondaki öğeleri geçirme olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="bb2d7-119">A `null` öğesi koleksiyonu ağaç üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="bb2d7-120">Eklenen bir öznitelik içeren öğe içinde benzersiz bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="bb2d7-121">Eklerken <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içerik üstü yoksa, ardından nesneleri yalnızca bağlı XML ağacına.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="bb2d7-122">Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, ardından yeni içerik kopyalanmış olan ve yeni kopyalanan içeriği XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="bb2d7-123">Belgeler için geçerli içerik</span><span class="sxs-lookup"><span data-stu-id="bb2d7-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="bb2d7-124">Öznitelikler ve basit içerik belgeye eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="bb2d7-125">Oluşturmak ihtiyacınız olan birçok senaryo yok bir <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="bb2d7-126">Bunun yerine, XML ağaçları genellikle oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> kök düğümü.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="bb2d7-127">Sürece belge (örneğin, işleme yönergeleri ve açıklamalar en üst düzeyinde oluşturmak zorunda veya belge türlerini desteklemek zorunda olduğundan) oluşturmak için belirli bir gereksiniminiz olmadığı, genellikle daha rahat kullanmak <xref:System.Xml.Linq.XElement> , kök düğümü olarak.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="bb2d7-128">Bir belge için geçerli içerik aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="bb2d7-128">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="bb2d7-129">Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="bb2d7-130">Belge türlerini öğeden önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-130">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="bb2d7-131">Sıfır veya bir öğe.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-131">Zero or one element.</span></span>  
  
-   <span data-ttu-id="bb2d7-132">Sıfır veya daha fazla açıklama.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-132">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="bb2d7-133">Sıfır veya daha fazla işleme yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-133">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="bb2d7-134">Yalnızca sıfır veya daha fazla metin düğümleri boşluk.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="bb2d7-135">Oluşturucular ve içerik eklemeye izin ver işlevleri</span><span class="sxs-lookup"><span data-stu-id="bb2d7-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="bb2d7-136">Alt içeriğin eklemek aşağıdaki yöntemlerden izin bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="bb2d7-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="bb2d7-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb2d7-137">Method</span></span>|<span data-ttu-id="bb2d7-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb2d7-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="bb2d7-139">Oluşturur bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="bb2d7-140">Oluşturur bir <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="bb2d7-141">Alt öğe içeriğini sonuna ekler <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="bb2d7-142">Sonra içerik ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="bb2d7-143">Önce içeriği ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="bb2d7-144">İçeriği, içerik alt başında ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="bb2d7-145">Tüm içeriğini (alt düğümleri ve öznitelikleri) yerini alan bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="bb2d7-146">Özniteliklerini değiştirir bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="bb2d7-147">Alt düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="bb2d7-148">Bir düğüm, yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb2d7-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb2d7-149">See Also</span></span>

- [<span data-ttu-id="bb2d7-150">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="bb2d7-150">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
