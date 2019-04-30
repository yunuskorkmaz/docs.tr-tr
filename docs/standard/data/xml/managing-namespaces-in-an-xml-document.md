---
title: XML Belgesinde Ad Alanlarını Yönetme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0ace73d81783852242a52bec006b0ad2edaadd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650199"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="25ace-102">XML Belgesinde Ad Alanlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="25ace-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="25ace-103">XML ad alanları XML belgesinde öğe ve öznitelik adları, özel ve önceden tanımlanmış bir URI'leri ile ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="25ace-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="25ace-104">Bu ilişkileri oluşturmak için URI ad alanı ön eklerini tanımlayın ve bu ön ekler öğe ve öznitelik adları XML verisindeki nitelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="25ace-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="25ace-105">Ad alanları, öğe ve öznitelik adı çakışmalarını önlemek ve öğeleri ve öznitelikleri aynı ada sahip işlenmesini ve farklı şekilde doğrulanmış etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="25ace-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="25ace-106">Ad alanlarını bildirme</span><span class="sxs-lookup"><span data-stu-id="25ace-106">Declaring namespaces</span></span>  
 <span data-ttu-id="25ace-107">Bir öğe üzerinde bir ad alanı bildirmek için kullanmanız `xmlns:` özniteliği:</span><span class="sxs-lookup"><span data-stu-id="25ace-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="25ace-108">Burada `<name>` ad alanı öneki ve `<"uri">` ad alanını tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="25ace-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="25ace-109">Önek bildirdikten sonra öğeleri ve özniteliklerinin bir XML belgesi sınıflandırmak ve ad alanı URI ile ilişkilendirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25ace-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="25ace-110">Ad alanı öneki belge kullanılmakta olduğundan uzunluğu kısa olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25ace-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="25ace-111">Bu örnek iki tanımlar `BOOK` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="25ace-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="25ace-112">Ön eke göre ilk öğeyi nitelenmiş `mybook`, ve ikinci öğe ön eke göre nitelenmiş `bb`.</span><span class="sxs-lookup"><span data-stu-id="25ace-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="25ace-113">Her ön eki farklı ad alanı URI ile ilişkilendirilir:</span><span class="sxs-lookup"><span data-stu-id="25ace-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="25ace-114">Bir öğenin belirli bir ad alanının bir parçası olduğunu belirtmek için ad alanı öneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="25ace-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="25ace-115">Örneğin, bir `Author` öğenin ait olduğu `mybook` ad alanı, bildirilen olarak `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="25ace-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="25ace-116">Bildirim kapsamı</span><span class="sxs-lookup"><span data-stu-id="25ace-116">Declaration scope</span></span>  
 <span data-ttu-id="25ace-117">Bir ad alanı içinde bildirilen öğe sonuna kadar bildirim noktasında etkilidir.</span><span class="sxs-lookup"><span data-stu-id="25ace-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="25ace-118">Bu örnekte ad alanı tanımlı `BOOK` öğesi öğeler için geçerli değildir `BOOK` öğesi gibi `Publisher` öğesi:</span><span class="sxs-lookup"><span data-stu-id="25ace-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="25ace-119">Bir ad alanı, kullanılabilir, ancak XML belgenin üst kısmında görünmesini yok önce bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="25ace-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="25ace-120">Bir XML belgesinde birden çok ad alanını kullandığınızda, bir ad alanı Temizleyicisi görünümlü bir belge oluşturmak için varsayılan ad alanı olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25ace-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="25ace-121">Varsayılan ad alanı, kök öğesi bildirilmiş ve belgedeki tüm nitelenmemiş öğeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25ace-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="25ace-122">Varsayılan ad alanlarını öznitelikler için yalnızca öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25ace-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="25ace-123">Varsayılan ad alanı kullanılacak önek ve virgül gelen öğede bildirimi atla:</span><span class="sxs-lookup"><span data-stu-id="25ace-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="25ace-124">Ad alanlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="25ace-124">Managing namespaces</span></span>  
 <span data-ttu-id="25ace-125"><xref:System.Xml.XmlNamespaceManager> Sınıf ad alanı URI koleksiyonunu depolar ve bunların ön ekleri ve sağlar, konum ekleyin ve bu koleksiyondan ad alanları.</span><span class="sxs-lookup"><span data-stu-id="25ace-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="25ace-126">Belirli bağlamlarda bu sınıfı daha iyi XML işlem performansı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="25ace-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="25ace-127">Örneğin, <xref:System.Xml.Xsl.XsltContext> sınıfının kullandığı <xref:System.Xml.XmlNamespaceManager> XPath desteği.</span><span class="sxs-lookup"><span data-stu-id="25ace-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="25ace-128">Ad alanı Yöneticisi'ni ad alanlarında herhangi doğrulaması gerçekleştirmez, ancak önek ve ad alanları zaten doğrulandı ve uygun varsayar [W3C ad alanları](https://www.w3.org/TR/REC-xml-names/) belirtimi.</span><span class="sxs-lookup"><span data-stu-id="25ace-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25ace-129">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) kullanmayın <xref:System.Xml.XmlNamespaceManager> ad alanlarını yönetmek için.</span><span class="sxs-lookup"><span data-stu-id="25ace-129">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="25ace-130">Bkz: [XML ad alanları ile çalışma (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) ve [(Visual Basic) XML ad alanları ile çalışma](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) LINQ to XML kullanarak ad alanlarını yönetme hakkında bilgi için LINQ belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="25ace-130">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="25ace-131">Bazı görevlerin ile gerçekleştirebileceğiniz yönetim ve arama <xref:System.Xml.XmlNamespaceManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="25ace-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="25ace-132">Daha fazla bilgi ve örnekler için her bir metot veya Özellik Başvurusu sayfasına bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="25ace-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="25ace-133">Bitiş</span><span class="sxs-lookup"><span data-stu-id="25ace-133">To</span></span>|<span data-ttu-id="25ace-134">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="25ace-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="25ace-135">Bir ad alanı Ekle</span><span class="sxs-lookup"><span data-stu-id="25ace-135">Add a namespace</span></span>|<span data-ttu-id="25ace-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25ace-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="25ace-137">Bir ad alanını Kaldır</span><span class="sxs-lookup"><span data-stu-id="25ace-137">Remove a namespace</span></span>|<span data-ttu-id="25ace-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25ace-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="25ace-139">Varsayılan ad alanı URI bulma</span><span class="sxs-lookup"><span data-stu-id="25ace-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="25ace-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="25ace-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="25ace-141">İçin bir ad alanı öneki URI bulma</span><span class="sxs-lookup"><span data-stu-id="25ace-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="25ace-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25ace-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="25ace-143">Ad alanı için URI öneki bulun</span><span class="sxs-lookup"><span data-stu-id="25ace-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="25ace-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25ace-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="25ace-145">Geçerli düğüm ad alanlarının listesini alın</span><span class="sxs-lookup"><span data-stu-id="25ace-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="25ace-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25ace-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="25ace-147">Bir ad alanı kapsamı</span><span class="sxs-lookup"><span data-stu-id="25ace-147">Scope a namespace</span></span>|<span data-ttu-id="25ace-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> ve <xref:System.Xml.XmlNamespaceManager.PopScope%2A> yöntemleri</span><span class="sxs-lookup"><span data-stu-id="25ace-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="25ace-149">Bir önek geçerli kapsamda tanımlı olup olmadığını denetleyin</span><span class="sxs-lookup"><span data-stu-id="25ace-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="25ace-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25ace-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="25ace-151">Ön ekleri ve URI'leri ara için kullanılan ad tablosu Al</span><span class="sxs-lookup"><span data-stu-id="25ace-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="25ace-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="25ace-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25ace-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25ace-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="25ace-154">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="25ace-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
