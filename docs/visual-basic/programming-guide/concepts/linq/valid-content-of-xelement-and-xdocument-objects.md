---
title: Geçerli içerik XElement ve XDocument Objects2
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: 4b1d588f0ebbfec6d5cf7a58b63f92005db75acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649389"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="d9832-102">Geçerli içerik XElement ve XDocument nesneleri</span><span class="sxs-lookup"><span data-stu-id="d9832-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="d9832-103">Bu konuda oluşturucular ve içerik öğelerini ve belgeleri eklemek için kullandığınız yöntemleri için geçirilen geçerli bağımsız değişkenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9832-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="d9832-104">Geçerli içerik</span><span class="sxs-lookup"><span data-stu-id="d9832-104">Valid Content</span></span>  
 <span data-ttu-id="d9832-105">Sorguları genellikle değerlendirmek için <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d9832-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="d9832-106">Koleksiyonları geçirebilir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri <xref:System.Xml.Linq.XElement> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="d9832-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="d9832-107">Bu nedenle, bir sorgunun sonuçlarını içeriği olarak yöntemlere ve XML ağaçları doldurmak için kullandığınız oluşturucular geçirmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="d9832-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="d9832-108">Basit içerik eklerken, çeşitli türleri bu yönteme geçirilen.</span><span class="sxs-lookup"><span data-stu-id="d9832-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="d9832-109">Geçerli türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d9832-109">Valid types include the following:</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   <span data-ttu-id="d9832-110">Uygulayan herhangi bir türü `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="d9832-110">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="d9832-111">Uygulayan herhangi bir türü <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d9832-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="d9832-112">Karmaşık içerik eklerken, çeşitli türleri bu yönteme geçirilen:</span><span class="sxs-lookup"><span data-stu-id="d9832-112">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   <span data-ttu-id="d9832-113">Uygulayan herhangi bir türü <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="d9832-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="d9832-114">Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>nesne koleksiyonunda numaralandırılan ve koleksiyondaki tüm öğeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9832-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="d9832-115">Koleksiyon içeriyorsa <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneleri, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9832-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="d9832-116">Koleksiyon metin (ya da metne dönüştürülecek nesneleri) içeriyorsa, koleksiyon metinde birleştirilmiş ve tek bir metin düğümü olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9832-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="d9832-117">İçerik `null`, hiçbir şey eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9832-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="d9832-118">Ne zaman bir koleksiyon öğelerini koleksiyonda geçirme olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="d9832-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="d9832-119">A `null` öğesi koleksiyonu ağaç üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="d9832-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="d9832-120">Eklenen bir öznitelik içeren öğe içinde benzersiz bir ad olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9832-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="d9832-121">Eklerken <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içeriğe üst öğeye sahipse, ardından nesneleri yalnızca bağlı XML ağacına.</span><span class="sxs-lookup"><span data-stu-id="d9832-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="d9832-122">Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, ardından yeni içerik kopyalanabilen ve yeni kopyalanmış içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9832-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="d9832-123">Belgeler için geçerli içerik</span><span class="sxs-lookup"><span data-stu-id="d9832-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="d9832-124">Öznitelikler ve basit içerik belgeye eklenemez.</span><span class="sxs-lookup"><span data-stu-id="d9832-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="d9832-125">Oluşturmak gereken birçok senaryo olmayan bir <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="d9832-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="d9832-126">Bunun yerine, XML ağaçlar olan genellikle oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> kök düğümü.</span><span class="sxs-lookup"><span data-stu-id="d9832-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="d9832-127">Sürece bir belge (örneğin, işleme yönergeleri ve açıklamalar en üst düzeyinde oluşturmak zorunda veya belge türlerini desteklemek zorunda olduğundan) oluşturmak için belirli bir gereksinim vardır, genellikle daha yararlıdır kullanmak uygun <xref:System.Xml.Linq.XElement> kök düğümü.</span><span class="sxs-lookup"><span data-stu-id="d9832-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="d9832-128">Bir belge için geçerli içerik aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="d9832-128">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="d9832-129">Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d9832-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="d9832-130">Belge türü öğeden önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="d9832-130">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="d9832-131">Sıfır veya bir öğe.</span><span class="sxs-lookup"><span data-stu-id="d9832-131">Zero or one element.</span></span>  
  
-   <span data-ttu-id="d9832-132">Sıfır veya daha fazla açıklama.</span><span class="sxs-lookup"><span data-stu-id="d9832-132">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="d9832-133">Sıfır veya daha fazla işleme yönergeler.</span><span class="sxs-lookup"><span data-stu-id="d9832-133">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="d9832-134">Yalnızca sıfır veya daha fazla metin düğümleri boşluk.</span><span class="sxs-lookup"><span data-stu-id="d9832-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="d9832-135">Oluşturucular ve içerik eklemeye izin ver işlevleri</span><span class="sxs-lookup"><span data-stu-id="d9832-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="d9832-136">Aşağıdaki yöntemlerden alt içeriği eklemenize izin bir <xref:System.Xml.Linq.XElement> veya bir <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="d9832-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="d9832-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d9832-137">Method</span></span>|<span data-ttu-id="d9832-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9832-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="d9832-139">Oluşturan bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d9832-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="d9832-140">Oluşturan bir <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="d9832-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="d9832-141">Alt öğe içeriğini sonuna ekler <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="d9832-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="d9832-142">Sonra içerik ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="d9832-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="d9832-143">Önce içeriği ekler <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="d9832-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="d9832-144">Alt öğe içeriğini başında içeriği ekler <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="d9832-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="d9832-145">Tüm içeriği (alt düğümleri ve öznitelikleri) değiştiren bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d9832-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="d9832-146">Özniteliklerini değiştirir bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d9832-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="d9832-147">Alt düğümler ile yeni içerik değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9832-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="d9832-148">Bir düğüm yeni içerikle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d9832-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9832-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9832-149">See Also</span></span>  
 [<span data-ttu-id="d9832-150">Oluşturma XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9832-150">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
