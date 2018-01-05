---
title: "Bir XML belgesi ad alanlarını yönetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7901f4bf88215f84445c1d222e6582e0a063c25a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="0fdb1-102">Bir XML belgesi ad alanlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="0fdb1-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="0fdb1-103">XML ad alanları, özel ve önceden tanımlanmış URI ile bir XML belgesi öğe ve öznitelik adları ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="0fdb1-104">Bu ilişkileri oluşturmak için ad alanı URI ön eklerini tanımlayın ve XML verileri öğe ve öznitelik adları nitelemek için ön eklerin kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="0fdb1-105">Ad alanları öğe ve öznitelik ad çakışmaları önlemek ve öğeleri ve özniteliklerinin aynı ada sahip işlenmesini ve farklı bir şekilde doğrulandı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="0fdb1-106">Ad alanlarını bildirme</span><span class="sxs-lookup"><span data-stu-id="0fdb1-106">Declaring namespaces</span></span>  
 <span data-ttu-id="0fdb1-107">Bir öğe üzerinde bir ad alanı bildirmek için kullandığınız `xmlns:` özniteliği:</span><span class="sxs-lookup"><span data-stu-id="0fdb1-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="0fdb1-108">Burada `<name>` ad alanı öneki ve `<"uri">` ad alanını tanımlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="0fdb1-109">Önek bildirme sonra öğeleri ve özniteliklerinin bir XML belgesi nitelemek ve ad alanı URI'si ile ilişkilendirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="0fdb1-110">Ad alanı öneki belge boyunca kullanıldığından uzunluğu kısa olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="0fdb1-111">Bu örnek iki tanımlar `BOOK` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="0fdb1-112">İlk öğe öğesi önekiyle tam `mybook`, ve ikinci öğe önekiyle tam `bb`.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-112">The first element element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="0fdb1-113">Her ön eki, farklı bir ad URI ile ilişkilidir:</span><span class="sxs-lookup"><span data-stu-id="0fdb1-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="0fdb1-114">Bir öğenin belirli bir ad alanının bir parçası olduğunu belirtmek için ad alanı önekini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="0fdb1-115">Örneğin, bir `Author` öğenin ait olduğu `mybook` ad alanı, onu bildirilen olarak `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="0fdb1-116">Bildirim kapsamı</span><span class="sxs-lookup"><span data-stu-id="0fdb1-116">Declaration scope</span></span>  
 <span data-ttu-id="0fdb1-117">Bir ad alanı bildiriminin içinde bildirilen öğesinin sonuna kadar noktasından etkili olur.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="0fdb1-118">Bu örnekte, ad alanı tanımlanan `BOOK` öğesi olmayan uygulama dışında öğelerine `BOOK` öğesi, gibi `Publisher` öğe:</span><span class="sxs-lookup"><span data-stu-id="0fdb1-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="0fdb1-119">Bir ad alanı kullanılabilir, ancak XML belgesi üstünde görüntülenecek yok önce bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="0fdb1-120">Birden çok ad alanını bir XML belgesi kullandığınızda, bir ad alanı temizleyici görünümlü bir belge oluşturmak için varsayılan ad alanı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="0fdb1-121">Varsayılan ad alanını kök öğesi içinde bildirilir ve belgedeki tüm nitelenmemiş öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="0fdb1-122">Varsayılan ad alanlarını yalnızca öğelerine öznitelikler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="0fdb1-123">Varsayılan ad alanını kullanmak için önek ve iki nokta üst üste öğesindeki bildirim alanından çıkarın:</span><span class="sxs-lookup"><span data-stu-id="0fdb1-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="0fdb1-124">Ad alanlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="0fdb1-124">Managing namespaces</span></span>  
 <span data-ttu-id="0fdb1-125"><xref:System.Xml.XmlNamespaceManager> Sınıfı ad alanı URI koleksiyonu depolar ve kendi önekleri ve yukarı, bakmanızı sağlayan ekleyin ve bu koleksiyondan ad alanlarını kaldırma.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="0fdb1-126">Bazı bağlamlarda bu sınıfı daha iyi XML işlem performansı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="0fdb1-127">Örneğin, <xref:System.Xml.Xsl.XsltContext> sınıfını kullanan <xref:System.Xml.XmlNamespaceManager> XPath desteği.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="0fdb1-128">Ad alanı manager ad alanında bulunan tüm doğrulaması gerçekleştirmez, ancak önekleri ve ad alanlarını zaten doğrulandı ve uygun varsayar [W3C ad alanları](http://www.w3.org/TR/REC-xml-names/) belirtimi.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](http://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fdb1-129">[LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) kullanmayan <xref:System.Xml.XmlNamespaceManager> ad alanlarını yönetmek için.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-129">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) doesn't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="0fdb1-130">Bkz: [XML ad alanları ile çalışma](http://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) LINQ belgelerinde LINQ-XML kullanırken ad alanlarını yönetme hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-130">See [Working with XML Namespaces](http://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="0fdb1-131">Bazı ile gerçekleştirebileceğiniz yönetimi ve arama görevleri <xref:System.Xml.XmlNamespaceManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="0fdb1-132">Daha fazla bilgi ve örnekler için her bir yöntemi veya özelliği için başvuru sayfası için bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="0fdb1-133">Bitiş</span><span class="sxs-lookup"><span data-stu-id="0fdb1-133">To</span></span>|<span data-ttu-id="0fdb1-134">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="0fdb1-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="0fdb1-135">Bir ad alanı Ekle</span><span class="sxs-lookup"><span data-stu-id="0fdb1-135">Add a namespace</span></span>|<span data-ttu-id="0fdb1-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fdb1-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="0fdb1-137">Bir ad alanı Kaldır</span><span class="sxs-lookup"><span data-stu-id="0fdb1-137">Remove a namespace</span></span>|<span data-ttu-id="0fdb1-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fdb1-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="0fdb1-139">Varsayılan ad alanı URI Bul</span><span class="sxs-lookup"><span data-stu-id="0fdb1-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="0fdb1-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>özelliği</span><span class="sxs-lookup"><span data-stu-id="0fdb1-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="0fdb1-141">URI bulmak için bir ad alanı öneki</span><span class="sxs-lookup"><span data-stu-id="0fdb1-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="0fdb1-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fdb1-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="0fdb1-143">Bir ad alanı için URI öneki Bul</span><span class="sxs-lookup"><span data-stu-id="0fdb1-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="0fdb1-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fdb1-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="0fdb1-145">Geçerli düğümdeki ad alanlarının listesini alın</span><span class="sxs-lookup"><span data-stu-id="0fdb1-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="0fdb1-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fdb1-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="0fdb1-147">Bir ad alanı kapsam</span><span class="sxs-lookup"><span data-stu-id="0fdb1-147">Scope a namespace</span></span>|<span data-ttu-id="0fdb1-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A>ve <xref:System.Xml.XmlNamespaceManager.PopScope%2A> yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0fdb1-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="0fdb1-149">Bir önek geçerli kapsamda tanımlı olup olmadığını denetleyin</span><span class="sxs-lookup"><span data-stu-id="0fdb1-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="0fdb1-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fdb1-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="0fdb1-151">Ön ekleri ve URI'ler aramak için kullanılan ad tablosunu Al</span><span class="sxs-lookup"><span data-stu-id="0fdb1-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="0fdb1-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A>özelliği</span><span class="sxs-lookup"><span data-stu-id="0fdb1-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fdb1-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0fdb1-153">See Also</span></span>  
 <xref:System.Xml.XmlNamespaceManager>  
 [<span data-ttu-id="0fdb1-154">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="0fdb1-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
