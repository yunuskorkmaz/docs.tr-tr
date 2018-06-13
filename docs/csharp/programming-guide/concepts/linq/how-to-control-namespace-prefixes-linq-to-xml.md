---
title: 'Nasıl yapılır: denetim Namespace önekleri (C#) (LINQ-XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: af864139d56bd3ebb22cca6369b82539b9d007da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327759"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="f53ea-102">Nasıl yapılır: denetim Namespace önekleri (C#) (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="f53ea-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="f53ea-103">Bu konuda, bir XML ağacı serileştirilirken ad alanı öneklerini nasıl denetleyebilirsiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f53ea-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="f53ea-104">Çoğu durumda, ad alanı öneklerini denetlemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f53ea-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="f53ea-105">Ancak, belirli XML programlamaya ad alanı önekleri belirli denetim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f53ea-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="f53ea-106">Örneğin, bir XSLT stil sayfası veya belirli bir ad alanı önekleri başvuran katıştırılmış XPath ifadeleri içeren bir XAML belgeyi düzenleme; Bu durumda, belge bu belirli öneklerle serileştirilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f53ea-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="f53ea-107">Ad alanı öneklerini denetlemek için kullanılan en yaygın nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="f53ea-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="f53ea-108">Ad alanı öneklerini denetlemek için başka bir ortak XML belgesi el ile düzenlemek istediğiniz ve yazmak kullanıcı için kolay ad alanı öneklerini oluşturmak istediğiniz nedeni.</span><span class="sxs-lookup"><span data-stu-id="f53ea-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="f53ea-109">Örneğin, bir XSD belge oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="f53ea-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="f53ea-110">Şemaları için kuralları önermek ya da kullanmak `xs` veya `xsd` Şema ad alanı öneki olarak.</span><span class="sxs-lookup"><span data-stu-id="f53ea-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="f53ea-111">Ad alanı öneklerini denetlemek için ad alanlarını bildirme öznitelikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f53ea-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="f53ea-112">Ad alanları belirli öneklerle bildirirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serileştirilirken ad alanı önekleri kabul dener.</span><span class="sxs-lookup"><span data-stu-id="f53ea-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="f53ea-113">Özniteliğin öznitelik adını ad oluşturduğunuz ad alanı öneki bildiren bir öznitelik oluşturmak için <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, ve ad alanı öneki öznitelik adıdır.</span><span class="sxs-lookup"><span data-stu-id="f53ea-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="f53ea-114">Ad alanı URI'si öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="f53ea-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f53ea-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f53ea-115">Example</span></span>  
 <span data-ttu-id="f53ea-116">Bu örnek iki ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="f53ea-116">This example declares two namespaces.</span></span> <span data-ttu-id="f53ea-117">Gerektiğini belirtir `http://www.adventure-works.com` ad alanı öneki var. `aw`ve `www.fourthcoffee.com` ad alanı öneki var. `fc`.</span><span class="sxs-lookup"><span data-stu-id="f53ea-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="f53ea-118">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="f53ea-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f53ea-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f53ea-119">See Also</span></span>  
 [<span data-ttu-id="f53ea-120">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f53ea-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
