---
description: 'Daha fazla bilgi edinin: XML şemaları oluşturma'
title: XML Şemaları Derleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: a748560b128ff16ea3cceb9be37e427396ec9dfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642623"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="3d599-103">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="3d599-103">Building XML Schemas</span></span>

<span data-ttu-id="3d599-104">Ad alanındaki sınıflar, <xref:System.Xml.Schema?displayProperty=nameWithType> World Wide Web Konsorsiyumu (W3C) XML şeması önerisi içinde tanımlanan yapılara eşlenir ve XML şemaları bellek içinde oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d599-104">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="3d599-105">XML şeması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d599-105">Building an XML Schema</span></span>  

 <span data-ttu-id="3d599-106">Aşağıdaki kod örneklerinde, SOM API 'SI, bellek içi bir müşteri XML şeması oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d599-106">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="3d599-107">Öğe ve öznitelikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d599-107">Creating Element and Attributes</span></span>  

 <span data-ttu-id="3d599-108">Kod örnekleri, aşağıdan yukarıya ait müşteri şemasını oluşturur, alt öğeleri, öznitelikleri ve önce karşılık gelen türlerini ve ardından üst düzey öğeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d599-108">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="3d599-109">Aşağıdaki kod örneğinde, `FirstName` ve `LastName` öğelerinin yanı sıra `CustomerId` Müşteri ŞEMASıNıN özniteliği de <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> som 'un ve sınıfları kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3d599-109">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="3d599-110"><xref:System.Xml.Schema.XmlSchemaElement.Name%2A> <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> Bir XML şeması içindeki ve öğelerinin "Name" özniteliğine karşılık gelen ve sınıflarının özelliklerinden ayrı `<xs:element />` `<xs:attribute />` olarak, şemanın (,, vb.) izin verdiği tüm diğer özniteliklerin `defaultValue` `fixedValue` `form` ve sınıflarında karşılık gelen özellikleri vardır <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3d599-110">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="3d599-111">Şema türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d599-111">Creating Schema Types</span></span>  

 <span data-ttu-id="3d599-112">Öğelerin ve özniteliklerin içeriği türlerine göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3d599-112">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="3d599-113">Türleri yerleşik şema türlerinden biri olan öğeler ve öznitelikler oluşturmak için, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> <xref:System.Xml.Schema.XmlSchemaElement> veya sınıflarının özelliği, <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfı kullanılarak yerleşik türün karşılık gelen nitelenmiş adı ile ayarlanır <xref:System.Xml.XmlQualifiedName> .</span><span class="sxs-lookup"><span data-stu-id="3d599-113">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="3d599-114">Öğeler ve öznitelikler için Kullanıcı tanımlı bir tür oluşturmak için veya sınıfı kullanılarak yeni bir basit veya karmaşık tür oluşturulur <xref:System.Xml.Schema.XmlSchemaSimpleType> <xref:System.Xml.Schema.XmlSchemaComplexType> .</span><span class="sxs-lookup"><span data-stu-id="3d599-114">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d599-115">Bir öğenin veya özniteliğin anonim alt öğeleri olan adlandırılmamış basit veya karmaşık türler oluşturmak için (yalnızca basit türler öznitelikler için geçerlidir), veya sınıflarının özelliğini <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> veya sınıflarının özelliği yerine adlandırılmamış basit veya karmaşık tür olarak ayarlayın <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3d599-115">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="3d599-116">XML şemaları hem anonim hem de adlandırılmış basit türlerin, diğer basit türlerden (yerleşik veya Kullanıcı tanımlı) kısıtlamasıyla türeme veya bir liste veya diğer basit türlerin birleşimi olarak oluşturulması için izin verir.</span><span class="sxs-lookup"><span data-stu-id="3d599-116">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="3d599-117"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>Sınıfı, yerleşik türü kısıtlayarak basit bir tür oluşturmak için kullanılır `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="3d599-117">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="3d599-118">Ayrıca, <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> veya <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> sınıflarını, liste veya birleşim türleri oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d599-118">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="3d599-119"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType>Özelliği, bir basit tür kısıtlaması, liste veya birleşim olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d599-119">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="3d599-120">Aşağıdaki kod örneğinde, `FirstName` öğesinin türü yerleşik türdür `xs:string` , `LastName` öğenin türü yerleşik türün kısıtlaması olan adlandırılmış basit bir türdür, bir `xs:string` `MaxLength` model değeri 20 ' dir ve `CustomerId` özniteliğin türü yerleşik bir türdür `xs:positiveInteger` ...</span><span class="sxs-lookup"><span data-stu-id="3d599-120">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="3d599-121">`Customer`Öğesi, parçacık `FirstName` ve öğelerinin dizisi olan `LastName` ve öznitelikleri özniteliğini içeren anonim bir karmaşık türdür `CustomerId` .</span><span class="sxs-lookup"><span data-stu-id="3d599-121">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d599-122">Ayrıca, <xref:System.Xml.Schema.XmlSchemaChoice> ya da <xref:System.Xml.Schema.XmlSchemaAll> sınıflarını yinelemek ya da semantiği için karmaşık türün parçacık olarak da kullanabilirsiniz `<xs:choice />` `<xs:all />` .</span><span class="sxs-lookup"><span data-stu-id="3d599-122">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="3d599-123">Şemaları oluşturma ve derleme</span><span class="sxs-lookup"><span data-stu-id="3d599-123">Creating and Compiling Schemas</span></span>  

 <span data-ttu-id="3d599-124">Bu noktada, alt öğeler ve öznitelikler, karşılık gelen türleri ve en üst düzey `Customer` öğe som API 'si kullanılarak bellek içinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="3d599-124">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="3d599-125">Aşağıdaki kod örneğinde, şema öğesi sınıfı kullanılarak oluşturulur <xref:System.Xml.Schema.XmlSchema> , en üst düzey öğeler ve türler özelliği kullanılarak buna eklenir <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> ve tam şema sınıfı kullanılarak derlenir <xref:System.Xml.Schema.XmlSchemaSet> ve konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="3d599-125">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="3d599-126"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType>Yöntemi, müşteri şemasını BIR XML şeması için kurallara göre doğrular ve şema sonrası derleme özelliklerini kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3d599-126">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d599-127">SOM API 'sindeki tüm şema sonrası derleme özellikleri, şema-doğrulama-bilgi kümesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="3d599-127">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="3d599-128"><xref:System.Xml.Schema.ValidationEventHandler>Öğesine eklenen, <xref:System.Xml.Schema.XmlSchemaSet> `ValidationCallback` şema doğrulama uyarılarını ve hatalarını işlemek için geri çağırma yöntemini çağıran bir temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="3d599-128">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="3d599-129">Aşağıdaki kod örneği ve konsola yazılan müşteri şeması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d599-129">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d599-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d599-130">See also</span></span>

- [<span data-ttu-id="3d599-131">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3d599-131">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="3d599-132">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="3d599-132">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="3d599-133">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="3d599-133">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="3d599-134">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="3d599-134">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="3d599-135">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="3d599-135">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="3d599-136">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3d599-136">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="3d599-137">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="3d599-137">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
