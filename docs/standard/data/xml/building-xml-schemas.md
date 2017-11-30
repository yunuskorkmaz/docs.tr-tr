---
title: "Yapı XML şemaları"
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
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e49c2130702fc7df223f2eab0ea0500b1c27b660
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="building-xml-schemas"></a><span data-ttu-id="88ff1-102">Yapı XML şemaları</span><span class="sxs-lookup"><span data-stu-id="88ff1-102">Building XML Schemas</span></span>
<span data-ttu-id="88ff1-103">Sınıflarda <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı World Wide Web Konsorsiyumu (W3C) XML Şeması öneri tanımlanan yapıları eşlemeniz ve XML şemaları bellek içi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88ff1-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="88ff1-104">Bir XML şeması oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ff1-104">Building an XML Schema</span></span>  
 <span data-ttu-id="88ff1-105">Aşağıdaki kod örneklerinde SOM API müşteri XML Şeması bellek içi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88ff1-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="88ff1-106">Öğe ve öznitelikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ff1-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="88ff1-107">Kod örnekleri, alt öğeleri, öznitelikleri ve bunların karşılık gelen türlerine ilk olarak, oluşturma şema, alt ve üst düzey öğeleri müşteri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88ff1-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="88ff1-108">Aşağıdaki kod örneğinde, `FirstName` ve `LastName` öğeleri yanı sıra `CustomerId` müşteri şeması özniteliği kullanılarak oluşturulan <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> SOM. sınıfları</span><span class="sxs-lookup"><span data-stu-id="88ff1-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="88ff1-109">Gelen apart <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> özelliklerini <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> "name" özniteliğinin değerini karşılık sınıfları `<xs:element />` ve `<xs:attribute />` şema tarafından izin verilen tüm diğer özniteliklerle bir XML Şeması öğelerini (`defaultValue`, `fixedValue`, `form`, vb.) karşılık gelen özelliklere sahip <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="88ff1-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="88ff1-110">Şema türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ff1-110">Creating Schema Types</span></span>  
 <span data-ttu-id="88ff1-111">İçerik öğeleri ve özniteliklerinin kendi türlerine göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="88ff1-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="88ff1-112">Öğeleri ve öznitelikleri olan türleridir yerleşik şema türlerinden birini oluşturmak için <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları kullanarak yerleşik türü, karşılık gelen tam adı ile ayarlamak <xref:System.Xml.XmlQualifiedName> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88ff1-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="88ff1-113">Kullanıcı tanımlı bir tür öğeleri ve öznitelikleri oluşturmak için yeni bir basit veya karmaşık türü kullanılarak oluşturulur <xref:System.Xml.Schema.XmlSchemaSimpleType> veya <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88ff1-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88ff1-114">Öğe veya öznitelik anonim alt Adlandırılmamış Basit veya karmaşık türleri oluşturmak için (yalnızca basit türler uygulamak için öznitelikler) ayarlamak <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> Adlandırılmamış Basit veya karmaşık türü sınıfları yerine <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="88ff1-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="88ff1-115">XML şemaları izin her ikisi de adsız ve adlandırılmış basit türler diğer basit türler (yerleşik veya kullanıcı tanımlı) kısıtlama yoluyla türetilmesi için veya bir liste veya diğer basit türler birleşimi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="88ff1-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="88ff1-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Sınıfı yerleşik kısıtlayarak basit bir tür oluşturmak için kullanılan `xs:string` türü.</span><span class="sxs-lookup"><span data-stu-id="88ff1-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="88ff1-117">Aynı zamanda <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> veya <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> liste veya birleşim türleri oluşturmak için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="88ff1-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="88ff1-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Özelliği, bir basit tür sınırlaması, liste veya birleşim olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88ff1-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="88ff1-119">Aşağıdaki kod örneğinde, `FirstName` öğenin türü olan yerleşik türü `xs:string`, `LastName` öğenin türü olan bir kısıtlamadır yerleşik türü adlandırılmış bir basit tür `xs:string`, ile bir `MaxLength` 20, model değeri ve `CustomerId` özniteliğin türü olan yerleşik türü `xs:positiveInteger`.</span><span class="sxs-lookup"><span data-stu-id="88ff1-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="88ff1-120">`Customer` Öğesidir, parçacık olduğunda dizisi anonim bir karmaşık tür olarak `FirstName` ve `LastName` öğelerini ve özniteliklerini içeren `CustomerId` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="88ff1-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88ff1-121">Aynı zamanda <xref:System.Xml.Schema.XmlSchemaChoice> veya <xref:System.Xml.Schema.XmlSchemaAll> çoğaltmak için karmaşık tür olarak parçacık sınıfları `<xs:choice />` veya `<xs:all />` semantiği.</span><span class="sxs-lookup"><span data-stu-id="88ff1-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="88ff1-122">Oluşturma ve şemaları derleme</span><span class="sxs-lookup"><span data-stu-id="88ff1-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="88ff1-123">Bu nokta, alt öğelerini ve özniteliklerini, bunların karşılık gelen türlerine ve üst düzey `Customer` öğesi bellekteki SOM API'si kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="88ff1-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="88ff1-124">Aşağıdaki kod örneğinde schema öğesi kullanılarak oluşturulan <xref:System.Xml.Schema.XmlSchema> sınıfı üst düzey öğeleri ve türleri eklenir kullanarak <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> özelliği ve tam şeması derlenmiş kullanarak <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve yazılır Konsolu.</span><span class="sxs-lookup"><span data-stu-id="88ff1-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="88ff1-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Yöntemi müşteri şemanın XML şeması için kuralları karşı doğrular ve sonrası schema derleme özellikler kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="88ff1-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88ff1-126">SOM API tüm sonrası schema derleme özelliklerinde sonrası-schema-doğrulama-bilgi farklı.</span><span class="sxs-lookup"><span data-stu-id="88ff1-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="88ff1-127"><xref:System.Xml.Schema.ValidationEventHandler> Eklenen <xref:System.Xml.Schema.XmlSchemaSet> geri çağırma yöntemini çağıran bir temsilci `ValidationCallback` şema doğrulama uyarıları ve hataları işlemek için.</span><span class="sxs-lookup"><span data-stu-id="88ff1-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="88ff1-128">Tam kod örneği ve konsola yazılan müşteri şeması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="88ff1-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="88ff1-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88ff1-129">See Also</span></span>  
 [<span data-ttu-id="88ff1-130">XML şema nesne modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="88ff1-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="88ff1-131">Okuma ve yazma XML şemaları</span><span class="sxs-lookup"><span data-stu-id="88ff1-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="88ff1-132">XML şemaları çapraz geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="88ff1-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="88ff1-133">XML şemaları düzenleme</span><span class="sxs-lookup"><span data-stu-id="88ff1-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="88ff1-134">Dahil olmak üzere veya XML şemalarını içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="88ff1-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="88ff1-135">Şema derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="88ff1-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="88ff1-136">Derleme sonrası şema bilgi</span><span class="sxs-lookup"><span data-stu-id="88ff1-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
