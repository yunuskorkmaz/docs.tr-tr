---
title: XML Şemaları Okuma ve Yazma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 889c5f85a2ea3fc08dadefda5509de0fcfab76ec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710420"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="635ec-102">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="635ec-102">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="635ec-103">Şema nesne modeli (SOM) API 'SI, dosyalardan veya diğer kaynaklardan XML şeması tanım dili (XSD) şemaları okumak ve yazmak ve World Wide Web Konsorsiyumu (W3C) XML şeması önerisi içinde tanımlanan yapılara eşlenen <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak XML şemaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="635ec-103">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="635ec-104">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="635ec-104">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="635ec-105"><xref:System.Xml.Schema.XmlSchema> sınıfı, XML şemaları okumak ve yazmak için <xref:System.Xml.Schema.XmlSchema.Read%2A> ve <xref:System.Xml.Schema.XmlSchema.Write%2A> yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="635ec-105">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="635ec-106"><xref:System.Xml.Schema.XmlSchema.Read%2A> yöntemi, XML şemasını temsil eden bir <xref:System.Xml.Schema.XmlSchema> nesnesi döndürür ve şema doğrulama uyarılarını işlemek için bir parametre olarak isteğe bağlı bir <xref:System.Xml.Schema.ValidationEventHandler> ve bir XML Şeması okunurken karşılaşılan hataları alır.</span><span class="sxs-lookup"><span data-stu-id="635ec-106">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="635ec-107"><xref:System.Xml.Schema.XmlSchema.Write%2A> yöntemi, <xref:System.IO.Stream>, <xref:System.IO.TextWriter> ve <xref:System.Xml.XmlWriter> nesnelerine XML şemaları Yazar ve isteğe bağlı bir <xref:System.Xml.XmlNamespaceManager> nesnesini parametre olarak alabilir.</span><span class="sxs-lookup"><span data-stu-id="635ec-107">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="635ec-108">Bir <xref:System.Xml.XmlNamespaceManager> bir XML şemasında karşılaşılan ad alanlarını işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="635ec-108">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="635ec-109"><xref:System.Xml.XmlNamespaceManager> sınıfı hakkında daha fazla bilgi için bkz. [XML belgesinde ad alanlarını yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="635ec-109">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="635ec-110">Aşağıdaki kod örneği, ve bir dosyasına XML şemaları okuma ve yazma hakkında bilgi gösterir.</span><span class="sxs-lookup"><span data-stu-id="635ec-110">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="635ec-111">Kod örneği `example.xsd` dosyayı alır, `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> yöntemini kullanarak dosyayı bir <xref:System.Xml.Schema.XmlSchema> nesnesine okur ve sonra dosyayı konsola ve yeni bir `new.xsd` dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="635ec-111">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="635ec-112">Kod örneği Ayrıca, XML Şeması okunurken herhangi bir şema doğrulama uyarısı veya hata ile karşılaşılan hataları işlemek için `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> metoduna parametre olarak bir <xref:System.Xml.Schema.ValidationEventHandler> sağlar.</span><span class="sxs-lookup"><span data-stu-id="635ec-112">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="635ec-113"><xref:System.Xml.Schema.ValidationEventHandler> belirtilmemişse (`null`), hiçbir uyarı veya hata bildirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="635ec-113">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="635ec-114">Örnek, `example.xsd` giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="635ec-114">The example takes the `example.xsd` as input.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="635ec-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="635ec-115">See also</span></span>

- [<span data-ttu-id="635ec-116">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="635ec-116">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="635ec-117">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="635ec-117">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="635ec-118">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="635ec-118">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="635ec-119">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="635ec-119">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="635ec-120">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="635ec-120">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="635ec-121">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="635ec-121">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="635ec-122">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="635ec-122">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
- [<span data-ttu-id="635ec-123">XML Belgesinde Ad Alanlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="635ec-123">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
