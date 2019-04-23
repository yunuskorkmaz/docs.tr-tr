---
title: XML Şemalarını Dahil Etme veya İçeri Aktarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45f6b402ae01b7f762f8ef10dcfb0bc46f949db6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343577"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="8b959-102">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="8b959-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="8b959-103">Bir XML Şeması içerebilir `<xs:import />`, `<xs:include />`, ve `<xs:redefine />` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="8b959-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="8b959-104">Bu şema öğeleri içerir veya bunları alır şemasının yapısı desteklemek için kullanılabilecek diğer XML şemaları bakın.</span><span class="sxs-lookup"><span data-stu-id="8b959-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="8b959-105"><xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> Ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıflarını, eşlemek için bu öğeleri içinde şema nesne modeli (SOM) API.</span><span class="sxs-lookup"><span data-stu-id="8b959-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="8b959-106">Dahil veya bir XML Şeması içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="8b959-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="8b959-107">Aşağıdaki kod örneği oluşturulan müşteri şema tamamlayan [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) adresi şemasıyla konu.</span><span class="sxs-lookup"><span data-stu-id="8b959-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="8b959-108">Adresi şemasını müşteri şemasıyla ek adres türleri müşteri şema kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8b959-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="8b959-109">Adresi şemasını kullanarak birleştirilebilir `<xs:include />` veya `<xs:import />` bileşenlerini adresi şeması olarak kullanılacak öğelerin- ya da kullanarak bir `<xs:redefine />` bileşenlerinin müşteri şema gerek uyacak şekilde değiştirmek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="8b959-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="8b959-110">Adresi şemasını sahip olduğu bir `targetNamespace` müşteri şema farklı `<xs:import />` öğesi ve bu nedenle alma semantiği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b959-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="8b959-111">Kod örneği, aşağıdaki adımlarda adresi şemasını içerir.</span><span class="sxs-lookup"><span data-stu-id="8b959-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="8b959-112">Müşteri şeması ve adresi şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesne ve bunları derler.</span><span class="sxs-lookup"><span data-stu-id="8b959-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="8b959-113">Herhangi bir şema doğrulama uyarıları ve okuma veya şemaları derlenirken karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="8b959-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="8b959-114">Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesneler için müşteri ve adresi şemalardan <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8b959-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="8b959-115">Şemaları derlendiğinden sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özellikleri erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b959-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="8b959-116">Oluşturur bir <xref:System.Xml.Schema.XmlSchemaImport> nesne, kümeleri <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> adresi Şema ad alanı için içeri aktarma özelliğini ayarlar <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> Al özelliğini <xref:System.Xml.Schema.XmlSchema> nesnesi adresi şemasının ve alma işlemi ekler <xref:System.Xml.Schema.XmlSchema.Includes%2A> Müşteri şeması özelliği.</span><span class="sxs-lookup"><span data-stu-id="8b959-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="8b959-117">Yeniden işler ve değiştirilmiş derler <xref:System.Xml.Schema.XmlSchema> şeması kullanarak müşteri nesnesi <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="8b959-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="8b959-118">Son olarak, yinelemeli olarak tüm konsol kullanarak müşteri Şemayı içeri aktarılan şema Yazar <xref:System.Xml.Schema.XmlSchema.Includes%2A> müşteri şema özelliği.</span><span class="sxs-lookup"><span data-stu-id="8b959-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="8b959-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A> Özelliği tüm erişim sağlar, içeri aktarmalar veya yeniden tanımlama bir şemaya eklenen içerir.</span><span class="sxs-lookup"><span data-stu-id="8b959-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="8b959-120">Tam kod örneği ve konsoluna yazılan müşteri ve adresi şemaları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b959-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="8b959-121">Hakkında daha fazla bilgi için `<xs:import />`, `<xs:include />`, ve `<xs:redefine />` öğeleri ve <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıfları için bkz [W3C XML Şeması](https://www.w3.org/XML/Schema) ve <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı sınıf başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="8b959-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b959-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b959-122">See also</span></span>

- [<span data-ttu-id="8b959-123">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8b959-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="8b959-124">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="8b959-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="8b959-125">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="8b959-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="8b959-126">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="8b959-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="8b959-127">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="8b959-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="8b959-128">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="8b959-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
