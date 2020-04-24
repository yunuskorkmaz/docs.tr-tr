---
title: XML Şemaları Derleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: c921331b00fe137d4ad52d62951e8c161768dfae
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711148"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="56637-102">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="56637-102">Building XML Schemas</span></span>
<span data-ttu-id="56637-103"><xref:System.Xml.Schema?displayProperty=nameWithType> Ad alanındaki sınıflar, world WIDE Web KONSORSIYUMU (W3C) XML şeması önerisi içinde tanımlanan yapılara EŞLENIR ve XML şemaları bellek içinde oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56637-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="56637-104">XML şeması oluşturma</span><span class="sxs-lookup"><span data-stu-id="56637-104">Building an XML Schema</span></span>  
 <span data-ttu-id="56637-105">Aşağıdaki kod örneklerinde, SOM API 'SI, bellek içi bir müşteri XML şeması oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56637-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="56637-106">Öğe ve öznitelikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="56637-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="56637-107">Kod örnekleri, aşağıdan yukarıya ait müşteri şemasını oluşturur, alt öğeleri, öznitelikleri ve önce karşılık gelen türlerini ve ardından üst düzey öğeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56637-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="56637-108">Aşağıdaki kod örneğinde `FirstName` , ve `LastName` öğelerinin yanı sıra MÜŞTERI şemasının `CustomerId` özniteliği de som 'un <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="56637-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="56637-109">Bir XML şeması <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> içindeki `<xs:element />` ve `<xs:attribute />` öğelerinin <xref:System.Xml.Schema.XmlSchemaElement> " <xref:System.Xml.Schema.XmlSchemaAttribute> Name" özniteliğine karşılık gelen ve sınıflarının özelliklerinden ayrı olarak, şemanın (`defaultValue`, `fixedValue`, `form`vb.) izin verdiği tüm diğer özniteliklerin <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> sınıflarında karşılık gelen özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="56637-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="56637-110">Şema türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="56637-110">Creating Schema Types</span></span>  
 <span data-ttu-id="56637-111">Öğelerin ve özniteliklerin içeriği türlerine göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="56637-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="56637-112">Türleri yerleşik şema türlerinden biri olan öğeler ve öznitelikler <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> oluşturmak için, <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıflarının özelliği, <xref:System.Xml.XmlQualifiedName> sınıfı kullanılarak yerleşik türün karşılık gelen nitelenmiş adı ile ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="56637-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="56637-113">Öğeler ve öznitelikler için Kullanıcı tanımlı bir tür oluşturmak için <xref:System.Xml.Schema.XmlSchemaSimpleType> veya <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı kullanılarak yeni bir basit veya karmaşık tür oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="56637-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56637-114">Bir öğenin veya özniteliğin anonim alt öğeleri olan adlandırılmamış basit veya karmaşık türler oluşturmak için (yalnızca basit türler öznitelikler için geçerlidir), veya sınıflarının özelliğini <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıflarının özelliği yerine <xref:System.Xml.Schema.XmlSchemaAttribute> adlandırılmamış basit veya karmaşık tür olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56637-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="56637-115">XML şemaları hem anonim hem de adlandırılmış basit türlerin, diğer basit türlerden (yerleşik veya Kullanıcı tanımlı) kısıtlamasıyla türeme veya bir liste veya diğer basit türlerin birleşimi olarak oluşturulması için izin verir.</span><span class="sxs-lookup"><span data-stu-id="56637-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="56637-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Sınıfı, yerleşik `xs:string` türü kısıtlayarak basit bir tür oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56637-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="56637-117">Ayrıca, veya <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> sınıflarını, <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> liste veya birleşim türleri oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56637-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="56637-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Özelliği, bir basit tür kısıtlaması, liste veya birleşim olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="56637-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="56637-119">`FirstName` Aşağıdaki kod örneğinde, öğesinin türü yerleşik türdür `xs:string`, `LastName` öğenin türü yerleşik türün `xs:string`kısıtlaması olan adlandırılmış basit bir türdür, bir `MaxLength` model değeri 20 ' dir ve `CustomerId` özniteliğin türü yerleşik bir türdür `xs:positiveInteger`...</span><span class="sxs-lookup"><span data-stu-id="56637-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="56637-120">`Customer` Öğesi, parçacık `FirstName` ve `LastName` öğelerinin dizisi olan ve öznitelikleri `CustomerId` özniteliğini içeren anonim bir karmaşık türdür.</span><span class="sxs-lookup"><span data-stu-id="56637-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56637-121">Ayrıca, <xref:System.Xml.Schema.XmlSchemaChoice> ya <xref:System.Xml.Schema.XmlSchemaAll> da sınıflarını yinelemek `<xs:choice />` ya `<xs:all />` da semantiği için karmaşık türün parçacık olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56637-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="56637-122">Şemaları oluşturma ve derleme</span><span class="sxs-lookup"><span data-stu-id="56637-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="56637-123">Bu noktada, alt öğeler ve öznitelikler, karşılık gelen türleri ve en üst düzey `Customer` öğe som API 'si kullanılarak bellek içinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="56637-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="56637-124">Aşağıdaki kod örneğinde, şema öğesi <xref:System.Xml.Schema.XmlSchema> sınıfı kullanılarak oluşturulur, en üst düzey öğeler ve türler <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> özelliği kullanılarak buna eklenir ve tam şema <xref:System.Xml.Schema.XmlSchemaSet> sınıfı kullanılarak derlenir ve konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="56637-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="56637-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Yöntemi, müşteri ŞEMASıNı bir XML şeması için kurallara göre doğrular ve şema sonrası derleme özelliklerini kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="56637-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56637-126">SOM API 'sindeki tüm şema sonrası derleme özellikleri, şema-doğrulama-bilgi kümesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="56637-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="56637-127">Öğesine <xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.Schema.XmlSchemaSet> eklenen, şema doğrulama uyarılarını ve hatalarını işlemek için geri çağırma `ValidationCallback` yöntemini çağıran bir temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="56637-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="56637-128">Aşağıdaki kod örneği ve konsola yazılan müşteri şeması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="56637-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56637-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56637-129">See also</span></span>

- [<span data-ttu-id="56637-130">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="56637-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="56637-131">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="56637-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="56637-132">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="56637-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="56637-133">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="56637-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="56637-134">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="56637-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="56637-135">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="56637-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="56637-136">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="56637-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
