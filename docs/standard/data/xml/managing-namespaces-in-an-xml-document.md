---
title: XML Belgesinde Ad Alanlarını Yönetme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: b60e773183bd008c99022946a2ec53932234fe23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289154"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="3da9a-102">XML Belgesinde Ad Alanlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="3da9a-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="3da9a-103">XML ad alanları, bir XML belgesindeki öğe ve öznitelik adlarını özel ve önceden tanımlanmış URI 'Ler ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="3da9a-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="3da9a-104">Bu ilişkilendirmeleri oluşturmak için, ad alanı URI 'Leri için ön ekleri tanımlar ve bu önekleri, XML verilerinde öğe ve öznitelik adlarını nitelemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3da9a-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="3da9a-105">Ad alanları öğe ve öznitelik adı çakışmalarını önler ve aynı ada sahip öğelerin ve özniteliklerin işlenmesini ve farklı şekilde doğrulanmasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="3da9a-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a><span data-ttu-id="3da9a-106">Ad alanlarını bildirme</span><span class="sxs-lookup"><span data-stu-id="3da9a-106">Declaring namespaces</span></span>  
 <span data-ttu-id="3da9a-107">Bir öğe üzerinde bir ad alanı bildirmek için `xmlns:` özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="3da9a-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="3da9a-108">Burada `<name>` ad alanı öneki ve `<"uri">` ad ALANıNı tanımlayan URI 'dir.</span><span class="sxs-lookup"><span data-stu-id="3da9a-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="3da9a-109">Ön eki bildirdikten sonra, bir XML belgesindeki öğeleri ve öznitelikleri nitelemek ve bunları ad alanı URI 'siyle ilişkilendirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3da9a-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="3da9a-110">Ad alanı ön eki bir belge boyunca kullanıldığından, bu değer kısa bir süre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3da9a-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="3da9a-111">Bu örnek iki `BOOK` öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3da9a-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="3da9a-112">İlk öğe önek tarafından nitelenir, `mybook` ve ikinci öğe önek tarafından nitelenir `bb` .</span><span class="sxs-lookup"><span data-stu-id="3da9a-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="3da9a-113">Her önek farklı bir ad alanı URI 'siyle ilişkilendirilir:</span><span class="sxs-lookup"><span data-stu-id="3da9a-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="3da9a-114">Bir öğenin belirli bir ad alanının parçası olduğunu belirtmek için, buna ad alanı öneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3da9a-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="3da9a-115">Örneğin, bir `Author` öğe `mybook` ad alanına aitse, olarak belirtilir `<mybook:Author>` .</span><span class="sxs-lookup"><span data-stu-id="3da9a-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>
## <a name="declaration-scope"></a><span data-ttu-id="3da9a-116">Bildirim kapsamı</span><span class="sxs-lookup"><span data-stu-id="3da9a-116">Declaration scope</span></span>  
 <span data-ttu-id="3da9a-117">Bir ad alanı, içinde bildirildiği öğenin sonuna kadar bildirim noktasından etkilidir.</span><span class="sxs-lookup"><span data-stu-id="3da9a-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="3da9a-118">Bu örnekte, öğesinde tanımlanan ad alanı öğesi gibi `BOOK` öğe dışındaki öğelere uygulanmaz `BOOK` `Publisher` :</span><span class="sxs-lookup"><span data-stu-id="3da9a-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="3da9a-119">Ad alanı kullanılmadan önce bildirilmelidir, ancak XML belgesinin en üstünde görünmesini gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3da9a-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="3da9a-120">Bir XML belgesinde birden çok ad alanı kullandığınızda, temizleyici bir arama belgesi oluşturmak için bir ad alanını varsayılan ad alanı olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3da9a-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="3da9a-121">Varsayılan ad alanı, kök öğesinde bildirilmiştir ve belgedeki tüm nitelenmemiş öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3da9a-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="3da9a-122">Varsayılan ad alanları özniteliklere değil yalnızca öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3da9a-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="3da9a-123">Varsayılan ad alanını kullanmak için, öneki ve öğesindeki bildiriminden iki nokta üst üste atlayın:</span><span class="sxs-lookup"><span data-stu-id="3da9a-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="3da9a-124">Ad alanlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="3da9a-124">Managing namespaces</span></span>  
 <span data-ttu-id="3da9a-125"><xref:System.Xml.XmlNamespaceManager>Sınıfı, bir ad alanı URI 'leri ve bunların ön eklerini depolar ve bu koleksiyonda ad alanlarını arayabilir, eklemenize ve kaldırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3da9a-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="3da9a-126">Bazı bağlamlarda, daha iyi XML işleme performansı için bu sınıf gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3da9a-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="3da9a-127">Örneğin, <xref:System.Xml.Xsl.XsltContext> sınıfı <xref:System.Xml.XmlNamespaceManager> XPath desteği için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3da9a-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="3da9a-128">Ad alanı Yöneticisi ad alanları üzerinde herhangi bir doğrulama gerçekleştirmez, ancak ön eklerin ve ad alanlarının zaten doğrulanmış olduğunu varsayar ve [W3C ad](https://www.w3.org/TR/REC-xml-names/) alanları belirtimine uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="3da9a-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3da9a-129">[C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ' de LINQ to XML [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) ve <xref:System.Xml.XmlNamespaceManager> ad alanlarını yönetmek için kullanmayın Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3da9a-129">LINQ TO XML in [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="3da9a-130">LINQ to XML kullanırken ad alanlarını yönetme hakkında bilgi için bkz. [XML ad alanları (C#) Ile çalışma](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) ve LINQ belgelerindeki [XML ad alanları (Visual Basic) ile](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) çalışma.</span><span class="sxs-lookup"><span data-stu-id="3da9a-130">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="3da9a-131">Sınıfı ile gerçekleştirebileceğiniz yönetim ve arama görevlerinin bazıları aşağıda verilmiştir <xref:System.Xml.XmlNamespaceManager> .</span><span class="sxs-lookup"><span data-stu-id="3da9a-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="3da9a-132">Daha fazla bilgi ve örnek için, her bir yöntem veya özellik için başvuru sayfasının bağlantılarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="3da9a-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="3da9a-133">Alıcı</span><span class="sxs-lookup"><span data-stu-id="3da9a-133">To</span></span>|<span data-ttu-id="3da9a-134">Kullanım</span><span class="sxs-lookup"><span data-stu-id="3da9a-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="3da9a-135">Ad alanı Ekle</span><span class="sxs-lookup"><span data-stu-id="3da9a-135">Add a namespace</span></span>|<span data-ttu-id="3da9a-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="3da9a-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="3da9a-137">Ad alanını kaldır</span><span class="sxs-lookup"><span data-stu-id="3da9a-137">Remove a namespace</span></span>|<span data-ttu-id="3da9a-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="3da9a-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="3da9a-139">Varsayılan ad alanı için URI 'yi bul</span><span class="sxs-lookup"><span data-stu-id="3da9a-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="3da9a-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>özelliði</span><span class="sxs-lookup"><span data-stu-id="3da9a-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="3da9a-141">Bir ad alanı öneki için URI bulma</span><span class="sxs-lookup"><span data-stu-id="3da9a-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="3da9a-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="3da9a-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="3da9a-143">Bir ad alanı URI 'sinin önekini bulma</span><span class="sxs-lookup"><span data-stu-id="3da9a-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="3da9a-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="3da9a-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="3da9a-145">Geçerli düğümdeki ad alanlarının listesini al</span><span class="sxs-lookup"><span data-stu-id="3da9a-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="3da9a-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="3da9a-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="3da9a-147">Ad alanı kapsamı</span><span class="sxs-lookup"><span data-stu-id="3da9a-147">Scope a namespace</span></span>|<span data-ttu-id="3da9a-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A>ve <xref:System.Xml.XmlNamespaceManager.PopScope%2A> yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3da9a-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="3da9a-149">Geçerli kapsamda bir ön ek tanımlanıp tanımlanmadığını denetleyin</span><span class="sxs-lookup"><span data-stu-id="3da9a-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="3da9a-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> yöntemi</span><span class="sxs-lookup"><span data-stu-id="3da9a-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="3da9a-151">Ön ekleri ve URI 'Leri aramak için kullanılan ad tablosunu alın</span><span class="sxs-lookup"><span data-stu-id="3da9a-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="3da9a-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A>özelliði</span><span class="sxs-lookup"><span data-stu-id="3da9a-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3da9a-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3da9a-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="3da9a-154">XML belgeleri ve verileri</span><span class="sxs-lookup"><span data-stu-id="3da9a-154">XML Documents and Data</span></span>](index.md)
