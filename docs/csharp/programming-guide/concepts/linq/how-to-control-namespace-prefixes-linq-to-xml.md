---
title: 'Nasıl yapılır: denetim Namespace önekleri (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: dd2a91fde868425cadbc395d6db0f913e2be600f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135126"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="6d10f-102">Nasıl yapılır: denetim Namespace önekleri (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6d10f-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="6d10f-103">Bu konuda bir XML ağacı serileştirilirken ad alanı öneklerini nasıl denetleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6d10f-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="6d10f-104">Çoğu durumda, ad alanı ön ekleri denetlemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6d10f-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="6d10f-105">Ancak, belirli bir XML programlama araçları, ad alanı öneklerini belirli denetim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6d10f-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="6d10f-106">Örneğin, bir XSLT stil sayfası veya özel ad alanı öneklerini başvuran katıştırılmış XPath ifadeleri içeren bir XAML belgesi işliyor; Bu durumda, belge bu belirli ön ekler ile seri hale getirilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6d10f-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="6d10f-107">Ad alanı ön ekleri denetlemek için en yaygın nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="6d10f-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="6d10f-108">Ad alanı ön ekleri denetlemek için başka bir yaygın nedeni, XML belgesi el ile düzenlemek için kullanıcıların istediğiniz ve kullanıcıdan için kullanışlı bir ad alanı öneklerini oluşturmak istediğiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="6d10f-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="6d10f-109">Örneğin, bir XSD belgesi oluşturulurken.</span><span class="sxs-lookup"><span data-stu-id="6d10f-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="6d10f-110">Şemaları için kuralları önerisi, ya da kullandığınız `xs` veya `xsd` Şema ad alanı ön eki olarak.</span><span class="sxs-lookup"><span data-stu-id="6d10f-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="6d10f-111">Ad alanı ön ekleri denetlemek için ad alanları belirtmesi öznitelikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d10f-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="6d10f-112">Belirli ön ekler ad alanları bildirirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ad alanı öneklerini serileştirilirken dikkate dener.</span><span class="sxs-lookup"><span data-stu-id="6d10f-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="6d10f-113">Bir ad alanı öneki bildiren bir öznitelik oluşturmak için öznitelik adı ad alanı olduğu bir öznitelik oluşturun. <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, ve öznitelik adı ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="6d10f-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="6d10f-114">Öznitelik ad alanı URI değeridir.</span><span class="sxs-lookup"><span data-stu-id="6d10f-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d10f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d10f-115">Example</span></span>  
 <span data-ttu-id="6d10f-116">Bu örnek iki ad alanları bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d10f-116">This example declares two namespaces.</span></span> <span data-ttu-id="6d10f-117">Belirtir `http://www.adventure-works.com` ad alanı öneki olan `aw`ve `www.fourthcoffee.com` ad alanı öneki olan `fc`.</span><span class="sxs-lookup"><span data-stu-id="6d10f-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="6d10f-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6d10f-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d10f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d10f-119">See Also</span></span>

- [<span data-ttu-id="6d10f-120">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="6d10f-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
