---
title: Ad alanı önekleri (C#) (LINQ - XML) nasıl kontrol ediletilir?
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141387"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="d3b0e-102">Ad alanı önekleri (C#) (LINQ - XML) nasıl kontrol ediletilir?</span><span class="sxs-lookup"><span data-stu-id="d3b0e-102">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="d3b0e-103">Bu konu, bir XML ağacını seri hale alırken ad alanı öneklerini nasıl denetebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="d3b0e-104">Birçok durumda, ad alanı önekleri denetlemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="d3b0e-105">Ancak, bazı XML programlama araçları ad alanı önekleri belirli bir denetim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="d3b0e-106">Örneğin, bir XSLT stil sayfasını veya belirli ad alanı öneklerine başvuran katıştırılmış XPath ifadeleri içeren bir XAML belgesini manipüle ediyor olabilirsiniz; bu durumda, belgenin bu özel öneklerle serihale edilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="d3b0e-107">Ad alanı öneklerini denetlemenin en yaygın nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="d3b0e-108">Ad alanı öneklerini denetlemenin bir diğer yaygın nedeni de, kullanıcıların XML belgesini el ile yeniden oluşturmasını ve kullanıcının yazması için uygun ad alanı önekleri oluşturmasını istemenizdir.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="d3b0e-109">Örneğin, bir XSD belgesi oluşturuyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="d3b0e-110">Şemalar için sözleşmeler, şema `xs` `xsd` ad alanı için önek olarak veya kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="d3b0e-111">Ad alanı öneklerini denetlemek için, ad alanlarını bildiren öznitelikler eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="d3b0e-112">Ad alanlarını belirli öneklerle bildirirseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] seri hale getirilirken ad alanı öneklerini onurlandırmaya çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="d3b0e-113">Önek ile bir ad alanı bildiren bir öznitelik oluşturmak için, öznitelik adının ad alanı ve <xref:System.Xml.Linq.XNamespace.Xmlns%2A>öznitelik adı ad alanı ad alanı öneki olduğu bir öznitelik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="d3b0e-114">Özniteliğin değeri ad alanının URI'sidir.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3b0e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3b0e-115">Example</span></span>  
 <span data-ttu-id="d3b0e-116">Bu örnekte iki ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-116">This example declares two namespaces.</span></span> <span data-ttu-id="d3b0e-117">Ad alanının `http://www.adventure-works.com` önekinin olduğunu ve `aw` `www.fourthcoffee.com` ad alanının '' önekinin `fc`olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="d3b0e-118">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d3b0e-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3b0e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b0e-119">See also</span></span>

- [<span data-ttu-id="d3b0e-120">İsim Alanlarına Genel Bakış (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d3b0e-120">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
