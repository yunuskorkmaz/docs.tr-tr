---
title: Ad alanı öneklerini denetleme-LINQ to XML
description: C# ve Visual Basic bir XML ağacını serileştirmek için ad alanı öneklerini denetleyebilirsiniz. Bunu yapmak için ad alanlarını bildiren öznitelikleri ekleyin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553021"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a><span data-ttu-id="133ff-104">Ad alanı ön eklerini denetleme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="133ff-104">How to control namespace prefixes (LINQ to XML)</span></span>

<span data-ttu-id="133ff-105">Bu makalede, C# ve Visual Basic bir XML ağacını serileştirilirken ad alanı öneklerini nasıl denetleyebileceğinizi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="133ff-105">This article describes how to control namespace prefixes when serializing an XML tree in C# and Visual Basic.</span></span>

<span data-ttu-id="133ff-106">Birçok durumda, ad alanı öneklerini denetlemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="133ff-106">In many situations, it's not necessary to control namespace prefixes.</span></span> <span data-ttu-id="133ff-107">Ancak, belirli XML programlama araçları bunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="133ff-107">However, certain XML programming tools require it.</span></span> <span data-ttu-id="133ff-108">Örneğin, bir XSLT stil sayfasını veya belirli ad alanı öneklerine başvuran katıştırılmış XPath ifadeleri içeren bir XAML belgesini düzenleme gibi olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="133ff-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes.</span></span> <span data-ttu-id="133ff-109">Böyle bir durumda, belgenin bu öneklerle serileştirilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="133ff-109">In such a case, it's important that the document be serialized with those prefixes.</span></span> <span data-ttu-id="133ff-110">Bu, ad alanı öneklerini denetlemenin yaygın bir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="133ff-110">This is a common reason for controlling namespace prefixes.</span></span>

<span data-ttu-id="133ff-111">Diğer bir nedenden dolayı, kullanıcıların XML belgesini el ile düzenlemesini ve Kullanıcı için uygun olan ad alanı önekleri oluşturmasını istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="133ff-111">Another reason is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="133ff-112">Örneğin, bir XSD belgesi oluşturuluyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="133ff-112">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="133ff-113">Şemaların kuralları `xs` `xsd` , şema ad alanı için önek olarak ya da ' i kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="133ff-113">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>

<span data-ttu-id="133ff-114">Ad alanı öneklerini denetlemek için ad alanlarını bildiren öznitelikleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="133ff-114">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="133ff-115">Ad alanlarını belirli öneklerle bildirirseniz LINQ to XML serileştirilirken ad alanı öneklerini kabul etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="133ff-115">If you declare the namespaces with specific prefixes, LINQ to XML will attempt to honor the namespace prefixes when serializing.</span></span>

<span data-ttu-id="133ff-116">Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliği adının ad alanının olduğu <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ve özniteliğin adı ad alanı öneki olan bir öznitelik oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="133ff-116">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="133ff-117">Özniteliğin değeri, ad alanının URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="133ff-117">The value of the attribute is the URI of the namespace.</span></span>

## <a name="example-create-two-namespaces-that-have-prefixes"></a><span data-ttu-id="133ff-118">Örnek: ön ekleri olan iki ad alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="133ff-118">Example: Create two namespaces that have prefixes</span></span>

<span data-ttu-id="133ff-119">Bu örnek iki ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="133ff-119">This example declares two namespaces.</span></span> <span data-ttu-id="133ff-120">`aw`Ad alanı için ön ek `http://www.adventure-works.com` ve `fc` `www.fourthcoffee.com` ad alanı öneki belirler.</span><span class="sxs-lookup"><span data-stu-id="133ff-120">It specifies the prefix `aw` for the `http://www.adventure-works.com` namespace, and the prefix `fc` for the `www.fourthcoffee.com` namespace.</span></span>

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

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="133ff-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="133ff-121">See also</span></span>

- [<span data-ttu-id="133ff-122">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="133ff-122">Namespaces overview</span></span>](namespaces-overview.md)
