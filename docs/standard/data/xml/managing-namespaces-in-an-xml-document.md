---
title: XML Belgesinde Ad Alanlarını Yönetme
description: Bir XML belgesinde ad alanlarını yönetmeyi öğrenin. XML ad alanları, bir XML belgesindeki öğe ve öznitelik adlarını özel ve önceden tanımlanmış URI 'Ler ile ilişkilendirir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 500c477eaa98b2858573e1012c62db4bc6c68137
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548097"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="92cdf-104">XML Belgesinde Ad Alanlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="92cdf-104">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="92cdf-105">XML ad alanları, bir XML belgesindeki öğe ve öznitelik adlarını özel ve önceden tanımlanmış URI 'Ler ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="92cdf-105">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="92cdf-106">Bu ilişkilendirmeleri oluşturmak için, ad alanı URI 'Leri için ön ekleri tanımlar ve bu önekleri, XML verilerinde öğe ve öznitelik adlarını nitelemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92cdf-106">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="92cdf-107">Ad alanları öğe ve öznitelik adı çakışmalarını önler ve aynı ada sahip öğelerin ve özniteliklerin işlenmesini ve farklı şekilde doğrulanmasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="92cdf-107">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a><span data-ttu-id="92cdf-108">Ad alanlarını bildirme</span><span class="sxs-lookup"><span data-stu-id="92cdf-108">Declaring namespaces</span></span>  
 <span data-ttu-id="92cdf-109">Bir öğe üzerinde bir ad alanı bildirmek için `xmlns:` özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="92cdf-109">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="92cdf-110">Burada `<name>` ad alanı öneki ve `<"uri">` ad ALANıNı tanımlayan URI 'dir.</span><span class="sxs-lookup"><span data-stu-id="92cdf-110">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="92cdf-111">Ön eki bildirdikten sonra, bir XML belgesindeki öğeleri ve öznitelikleri nitelemek ve bunları ad alanı URI 'siyle ilişkilendirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92cdf-111">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="92cdf-112">Ad alanı ön eki bir belge boyunca kullanıldığından, bu değer kısa bir süre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92cdf-112">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="92cdf-113">Bu örnek iki `BOOK` öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="92cdf-113">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="92cdf-114">İlk öğe önek tarafından nitelenir, `mybook` ve ikinci öğe önek tarafından nitelenir `bb` .</span><span class="sxs-lookup"><span data-stu-id="92cdf-114">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="92cdf-115">Her önek farklı bir ad alanı URI 'siyle ilişkilendirilir:</span><span class="sxs-lookup"><span data-stu-id="92cdf-115">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="92cdf-116">Bir öğenin belirli bir ad alanının parçası olduğunu belirtmek için, buna ad alanı öneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92cdf-116">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="92cdf-117">Örneğin, bir `Author` öğe `mybook` ad alanına aitse, olarak belirtilir `<mybook:Author>` .</span><span class="sxs-lookup"><span data-stu-id="92cdf-117">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>
## <a name="declaration-scope"></a><span data-ttu-id="92cdf-118">Bildirim kapsamı</span><span class="sxs-lookup"><span data-stu-id="92cdf-118">Declaration scope</span></span>  
 <span data-ttu-id="92cdf-119">Bir ad alanı, içinde bildirildiği öğenin sonuna kadar bildirim noktasından etkilidir.</span><span class="sxs-lookup"><span data-stu-id="92cdf-119">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="92cdf-120">Bu örnekte, öğesinde tanımlanan ad alanı öğesi gibi `BOOK` öğe dışındaki öğelere uygulanmaz `BOOK` `Publisher` :</span><span class="sxs-lookup"><span data-stu-id="92cdf-120">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="92cdf-121">Ad alanı kullanılmadan önce bildirilmelidir, ancak XML belgesinin en üstünde görünmesini gerekmez.</span><span class="sxs-lookup"><span data-stu-id="92cdf-121">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="92cdf-122">Bir XML belgesinde birden çok ad alanı kullandığınızda, temizleyici bir arama belgesi oluşturmak için bir ad alanını varsayılan ad alanı olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92cdf-122">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="92cdf-123">Varsayılan ad alanı, kök öğesinde bildirilmiştir ve belgedeki tüm nitelenmemiş öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="92cdf-123">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="92cdf-124">Varsayılan ad alanları özniteliklere değil yalnızca öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="92cdf-124">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="92cdf-125">Varsayılan ad alanını kullanmak için, öneki ve öğesindeki bildiriminden iki nokta üst üste atlayın:</span><span class="sxs-lookup"><span data-stu-id="92cdf-125">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="92cdf-126">Ad alanlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="92cdf-126">Managing namespaces</span></span>  
 <span data-ttu-id="92cdf-127"><xref:System.Xml.XmlNamespaceManager>Sınıfı, bir ad alanı URI 'leri ve bunların ön eklerini depolar ve bu koleksiyonda ad alanlarını arayabilir, eklemenize ve kaldırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="92cdf-127">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="92cdf-128">Bazı bağlamlarda, daha iyi XML işleme performansı için bu sınıf gereklidir.</span><span class="sxs-lookup"><span data-stu-id="92cdf-128">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="92cdf-129">Örneğin, <xref:System.Xml.Xsl.XsltContext> sınıfı <xref:System.Xml.XmlNamespaceManager> XPath desteği için kullanır.</span><span class="sxs-lookup"><span data-stu-id="92cdf-129">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="92cdf-130">Ad alanı Yöneticisi ad alanları üzerinde herhangi bir doğrulama gerçekleştirmez, ancak ön eklerin ve ad alanlarının zaten doğrulanmış olduğunu varsayar ve [W3C ad](https://www.w3.org/TR/REC-xml-names/) alanları belirtimine uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="92cdf-130">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92cdf-131">[C#](../../linq/linq-xml-overview.md) ' de LINQ to XML [Visual Basic](../../linq/linq-xml-overview.md) ve <xref:System.Xml.XmlNamespaceManager> ad alanlarını yönetmek için kullanmayın Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="92cdf-131">LINQ TO XML in [C#](../../linq/linq-xml-overview.md) and [Visual Basic](../../linq/linq-xml-overview.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="92cdf-132">LINQ to XML kullanırken ad alanlarını yönetme hakkında bilgi için bkz. [XML ad alanları (C#) Ile çalışma](../../linq/namespaces-overview.md) ve LINQ belgelerindeki [XML ad alanları (Visual Basic) ile](../../linq/namespaces-overview.md) çalışma.</span><span class="sxs-lookup"><span data-stu-id="92cdf-132">See [Working with XML Namespaces (C#)](../../linq/namespaces-overview.md) and [Working with XML Namespaces (Visual Basic)](../../linq/namespaces-overview.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="92cdf-133">Sınıfı ile gerçekleştirebileceğiniz yönetim ve arama görevlerinin bazıları aşağıda verilmiştir <xref:System.Xml.XmlNamespaceManager> .</span><span class="sxs-lookup"><span data-stu-id="92cdf-133">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="92cdf-134">Daha fazla bilgi ve örnek için, her bir yöntem veya özellik için başvuru sayfasının bağlantılarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="92cdf-134">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="92cdf-135">Amaç</span><span class="sxs-lookup"><span data-stu-id="92cdf-135">To</span></span>|<span data-ttu-id="92cdf-136">Kullanın</span><span class="sxs-lookup"><span data-stu-id="92cdf-136">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="92cdf-137">Ad alanı Ekle</span><span class="sxs-lookup"><span data-stu-id="92cdf-137">Add a namespace</span></span>|<span data-ttu-id="92cdf-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="92cdf-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="92cdf-139">Ad alanını kaldır</span><span class="sxs-lookup"><span data-stu-id="92cdf-139">Remove a namespace</span></span>|<span data-ttu-id="92cdf-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="92cdf-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="92cdf-141">Varsayılan ad alanı için URI 'yi bul</span><span class="sxs-lookup"><span data-stu-id="92cdf-141">Find the URI for the default namespace</span></span>|<span data-ttu-id="92cdf-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> özelliði</span><span class="sxs-lookup"><span data-stu-id="92cdf-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="92cdf-143">Bir ad alanı öneki için URI bulma</span><span class="sxs-lookup"><span data-stu-id="92cdf-143">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="92cdf-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="92cdf-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="92cdf-145">Bir ad alanı URI 'sinin önekini bulma</span><span class="sxs-lookup"><span data-stu-id="92cdf-145">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="92cdf-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="92cdf-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="92cdf-147">Geçerli düğümdeki ad alanlarının listesini al</span><span class="sxs-lookup"><span data-stu-id="92cdf-147">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="92cdf-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="92cdf-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="92cdf-149">Ad alanı kapsamı</span><span class="sxs-lookup"><span data-stu-id="92cdf-149">Scope a namespace</span></span>|<span data-ttu-id="92cdf-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> ve <xref:System.Xml.XmlNamespaceManager.PopScope%2A> yöntemleri</span><span class="sxs-lookup"><span data-stu-id="92cdf-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="92cdf-151">Geçerli kapsamda bir ön ek tanımlanıp tanımlanmadığını denetleyin</span><span class="sxs-lookup"><span data-stu-id="92cdf-151">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="92cdf-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="92cdf-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="92cdf-153">Ön ekleri ve URI 'Leri aramak için kullanılan ad tablosunu alın</span><span class="sxs-lookup"><span data-stu-id="92cdf-153">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="92cdf-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> özelliði</span><span class="sxs-lookup"><span data-stu-id="92cdf-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92cdf-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92cdf-155">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="92cdf-156">XML belgeleri ve verileri</span><span class="sxs-lookup"><span data-stu-id="92cdf-156">XML Documents and Data</span></span>](index.md)
