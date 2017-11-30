---
title: "Okuma ve yazma XML şemaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aaf63acbb58fd86f7fa9a5dc3dce7508d90cfada
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="a6434-102">Okuma ve yazma XML şemaları</span><span class="sxs-lookup"><span data-stu-id="a6434-102">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="a6434-103">Şema nesne modeli (SOM) API okumak ve XML Şeması Tanım Dili (XSD) şemaları dosyaları veya diğer kaynakları yazma ve XML şemaları sınıflarda kullanarak bellek içi oluşturmak için kullanılan <xref:System.Xml.Schema?displayProperty=nameWithType> dünyada tanımlanan yapıları Eşle ad alanı Wide Web Konsorsiyumu (W3C) XML Şeması öneri.</span><span class="sxs-lookup"><span data-stu-id="a6434-103">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="a6434-104">Okuma ve yazma XML şemaları</span><span class="sxs-lookup"><span data-stu-id="a6434-104">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="a6434-105"><xref:System.Xml.Schema.XmlSchema> SAX <xref:System.Xml.Schema.XmlSchema.Read%2A> ve <xref:System.Xml.Schema.XmlSchema.Write%2A> XML şemaları okumasına ve yazmasına yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a6434-105">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="a6434-106"><xref:System.Xml.Schema.XmlSchema.Read%2A> Yöntemi döndürür bir <xref:System.Xml.Schema.XmlSchema> XML Şeması temsil eden nesne ve isteğe bağlı bir alan <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama uyarıları ve XML Şeması okunurken karşılaşılan hataları işlemek için bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="a6434-106">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="a6434-107"><xref:System.Xml.Schema.XmlSchema.Write%2A> Yöntemi için XML şemaları Yazar <xref:System.IO.Stream>, <xref:System.IO.TextWriter> ve <xref:System.Xml.XmlWriter> nesneleri ve isteğe bağlı bir alabilir <xref:System.Xml.XmlNamespaceManager> nesnesini parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="a6434-107">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="a6434-108">Bir <xref:System.Xml.XmlNamespaceManager> ad alanları bir XML Şeması karşılaştı işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6434-108">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="a6434-109">Hakkında daha fazla bilgi için <xref:System.Xml.XmlNamespaceManager> sınıfı için bkz: [ad alanları bir XML belgesi yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="a6434-109">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="a6434-110">Aşağıdaki kod örneğinde, okuma ve XML şemaları gelen ve bir dosyaya yazma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6434-110">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="a6434-111">Kod örneği alır `example.xsd` dosyası içine okur bir <xref:System.Xml.Schema.XmlSchema> kullanarak nesne `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> yöntemi ve ardından konsolu ve yeni bir dosya Yazar `new.xsd` dosya.</span><span class="sxs-lookup"><span data-stu-id="a6434-111">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="a6434-112">Kod örneği de sağlar bir <xref:System.Xml.Schema.ValidationEventHandler> bir parametre olarak `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> herhangi bir şema doğrulama uyarıları veya XML Şeması okunurken karşılaşılan hataları işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="a6434-112">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="a6434-113">Varsa <xref:System.Xml.Schema.ValidationEventHandler> belirtilmemiş (`null`), hiçbir uyarı veya hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="a6434-113">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="a6434-114">Örnek alır `example.xsd` giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="a6434-114">The example takes the `example.xsd` as input.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6434-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6434-115">See Also</span></span>  
 [<span data-ttu-id="a6434-116">XML şema nesne modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="a6434-116">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="a6434-117">Yapı XML şemaları</span><span class="sxs-lookup"><span data-stu-id="a6434-117">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="a6434-118">XML şemaları çapraz geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="a6434-118">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="a6434-119">XML şemaları düzenleme</span><span class="sxs-lookup"><span data-stu-id="a6434-119">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="a6434-120">Dahil olmak üzere veya XML şemalarını içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="a6434-120">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="a6434-121">Şema derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="a6434-121">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="a6434-122">Derleme sonrası şema bilgi</span><span class="sxs-lookup"><span data-stu-id="a6434-122">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [<span data-ttu-id="a6434-123">Bir XML belgesi ad alanlarını yönetme</span><span class="sxs-lookup"><span data-stu-id="a6434-123">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
