---
title: XML Şemaları Okuma ve Yazma
description: Şema nesne modeli (SOM) API 'sini kullanarak, .NET 'teki dosyalardan veya diğer kaynaklardan XML şeması tanım dili (XSD) şemalarını okuyun ve yazın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: ae951efafd68d0ddf4f74876edd4c12564d68dde
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830889"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="7c4f3-103">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="7c4f3-103">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="7c4f3-104">Şema nesne modeli (SOM) API 'SI, dosyalardan veya diğer kaynaklardan XML şeması tanım dili (XSD) şemalarını okumak ve yazmak ve <xref:System.Xml.Schema?displayProperty=nameWithType> World Wide Web Konsorsiyumu (W3C) XML şeması önerisi içinde tanımlanan yapılara eşlenen ad alanındaki sınıfları kullanarak XML şemaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-104">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="7c4f3-105">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="7c4f3-105">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="7c4f3-106"><xref:System.Xml.Schema.XmlSchema>Sınıfı, <xref:System.Xml.Schema.XmlSchema.Read%2A> ve <xref:System.Xml.Schema.XmlSchema.Write%2A> XML şemaları okumak ve yazmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-106">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="7c4f3-107"><xref:System.Xml.Schema.XmlSchema.Read%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchema> XML şemasını temsil eden bir nesne döndürür ve <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama UYARıLARıNı ve bir XML Şeması okunurken karşılaşılan hataları işlemek için isteğe bağlı olarak bir parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-107">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="7c4f3-108"><xref:System.Xml.Schema.XmlSchema.Write%2A>Yöntemi <xref:System.IO.Stream> , ve nesnelerine XML şemaları Yazar <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> ve isteğe bağlı bir <xref:System.Xml.XmlNamespaceManager> nesneyi parametre olarak alabilir.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-108">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="7c4f3-109">Bir <xref:System.Xml.XmlNamespaceManager> XML şemasında karşılaşılan ad alanlarını işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-109">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="7c4f3-110">Sınıfı hakkında daha fazla bilgi için <xref:System.Xml.XmlNamespaceManager> bkz. [XML belgesinde ad alanlarını yönetme](managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="7c4f3-110">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="7c4f3-111">Aşağıdaki kod örneği, ve bir dosyasına XML şemaları okuma ve yazma hakkında bilgi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-111">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="7c4f3-112">Kod örneği `example.xsd` dosyayı alır, <xref:System.Xml.Schema.XmlSchema> yöntemini kullanarak bir nesnesine okur `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> ve sonra dosyayı konsola ve yeni bir `new.xsd` dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-112">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="7c4f3-113">Kod örneği Ayrıca, <xref:System.Xml.Schema.ValidationEventHandler> `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> XML şemasını okurken herhangi bir şema doğrulama uyarısı veya hata ile karşılaşılan hataları işlemek için yöntemine bir parametre olarak da sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-113">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="7c4f3-114">Belirtilmemişse, <xref:System.Xml.Schema.ValidationEventHandler> `null` hiçbir uyarı veya hata bildirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-114">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="7c4f3-115">Örnek, `example.xsd` giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-115">The example takes the `example.xsd` as input.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c4f3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c4f3-116">See also</span></span>

- [<span data-ttu-id="7c4f3-117">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7c4f3-117">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="7c4f3-118">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="7c4f3-118">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="7c4f3-119">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="7c4f3-119">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="7c4f3-120">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="7c4f3-120">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="7c4f3-121">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="7c4f3-121">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="7c4f3-122">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="7c4f3-122">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="7c4f3-123">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="7c4f3-123">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
- [<span data-ttu-id="7c4f3-124">XML Belgesinde Ad Alanlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="7c4f3-124">Managing Namespaces in an XML Document</span></span>](managing-namespaces-in-an-xml-document.md)
