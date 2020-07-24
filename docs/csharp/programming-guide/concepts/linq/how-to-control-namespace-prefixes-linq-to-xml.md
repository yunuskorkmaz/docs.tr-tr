---
title: Ad alanı öneklerini denetleme (C#) (LINQ to XML)
description: C# ' de LINQ to XML bir XML ağacını serileştirilirken ad alanı öneklerini nasıl denetleyeceğinizi öğrenin. Bazı durumlar, ad alanı önekleri denetimi gerektirir.
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: b0c5cbfa7488f3a7105595830ef6765e6bfb1f12
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105304"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="eb2e6-104">Ad alanı öneklerini denetleme (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="eb2e6-104">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="eb2e6-105">Bu konu, bir XML ağacını serileştirilirken ad alanı öneklerini nasıl denetleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-105">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="eb2e6-106">Birçok durumda, ad alanı öneklerini denetlemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-106">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="eb2e6-107">Ancak bazı XML programlama araçları, ad alanı önekleri için belirli bir denetim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-107">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="eb2e6-108">Örneğin, bir XSLT stil sayfasını veya belirli ad alanı öneklerine başvuran gömülü XPath ifadeleri içeren bir XAML belgesini düzenleme Bu durumda, belgenin bu özel öneklerle serileştirilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="eb2e6-109">Bu, ad alanı öneklerini denetlemenin en yaygın nedenidir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-109">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="eb2e6-110">Ad alanı öneklerini denetlemenin bir diğer yaygın nedeni, kullanıcıların XML belgesini el ile düzenlemesini ve kullanıcının yazması için uygun olan ad alanı önekleri oluşturmasını istemesidir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-110">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="eb2e6-111">Örneğin, bir XSD belgesi oluşturuluyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-111">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="eb2e6-112">Şemaların kuralları `xs` `xsd` , şema ad alanı için önek olarak ya da ' i kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-112">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="eb2e6-113">Ad alanı öneklerini denetlemek için ad alanlarını bildiren öznitelikleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-113">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="eb2e6-114">Ad alanlarını belirli öneklerle bildirirseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serileştirilirken ad alanı öneklerini kabul etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-114">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="eb2e6-115">Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliği adının ad alanının olduğu <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ve özniteliğin adı ad alanı öneki olan bir öznitelik oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-115">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="eb2e6-116">Özniteliğin değeri, ad alanının URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-116">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb2e6-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb2e6-117">Example</span></span>  
 <span data-ttu-id="eb2e6-118">Bu örnek iki ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-118">This example declares two namespaces.</span></span> <span data-ttu-id="eb2e6-119">`http://www.adventure-works.com`Ad alanının öneki olduğunu `aw` ve `www.fourthcoffee.com` ad alanının öneki olduğunu belirtir `fc` .</span><span class="sxs-lookup"><span data-stu-id="eb2e6-119">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="eb2e6-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="eb2e6-120">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb2e6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb2e6-121">See also</span></span>

- [<span data-ttu-id="eb2e6-122">Ad alanlarına genel bakış (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="eb2e6-122">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
