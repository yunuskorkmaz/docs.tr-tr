---
title: XML Şemalarını Düzenleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: d7d9f8e0d4ec2f343b50e68e942bf94e93576f25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710953"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="bb274-102">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="bb274-102">Editing XML Schemas</span></span>

<span data-ttu-id="bb274-103">XML şeması düzenlenmesinin, şema nesne modeli 'nin (SOM) en önemli özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="bb274-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="bb274-104">SOM 'un şema öncesi derleme özelliklerinin tümü bir XML şemasında varolan değerleri değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb274-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="bb274-105">XML şeması daha sonra değişiklikleri yansıtacak şekilde yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="bb274-105">The XML schema can then be recompiled to reflect the changes.</span></span>

<span data-ttu-id="bb274-106">SOM 'a yüklenen bir şemayı düzenlemenin ilk adımı şemanın gezedir.</span><span class="sxs-lookup"><span data-stu-id="bb274-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="bb274-107">Bir şemayı düzenlemeye çalışmadan önce, SOM API 'sini kullanarak bir şemanın geçiş yapmaya alışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb274-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="bb274-108">Şema-derleme-bilgi kümesi 'nin (PSCı) ön ve son şema-derleme özelliklerini de tanımanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb274-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>

## <a name="editing-an-xml-schema"></a><span data-ttu-id="bb274-109">XML şeması düzenleniyor</span><span class="sxs-lookup"><span data-stu-id="bb274-109">Editing an XML Schema</span></span>

<span data-ttu-id="bb274-110">Bu bölümde, iki kod örneği sağlanır, ikisi de [derleme XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) içinde oluşturulan müşteri şemasını düzenler konu.</span><span class="sxs-lookup"><span data-stu-id="bb274-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="bb274-111">İlk kod örneği, `Customer` öğesine yeni bir `PhoneNumber` öğesi ekler ve ikinci kod örneği, `FirstName` öğesine yeni bir `Title` özniteliği ekler.</span><span class="sxs-lookup"><span data-stu-id="bb274-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="bb274-112">İlk örnek ayrıca, ikinci kod örneği şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonunu kullandığında, bu, müşteri şemasına geçme yöntemi olarak şema sonrası-derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb274-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

### <a name="phonenumber-element-example"></a><span data-ttu-id="bb274-113">PhoneNumber öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="bb274-113">PhoneNumber Element Example</span></span>

<span data-ttu-id="bb274-114">Bu ilk kod örneği, müşteri şemasının `Customer` öğesine yeni bir `PhoneNumber` öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="bb274-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="bb274-115">Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.</span><span class="sxs-lookup"><span data-stu-id="bb274-115">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="bb274-116">Yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesine müşteri şemasını ekler ve sonra derler.</span><span class="sxs-lookup"><span data-stu-id="bb274-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="bb274-117">Şemayı okuma veya derleme ile karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilcisi tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="bb274-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="bb274-118"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini çağırarak <xref:System.Xml.Schema.XmlSchemaSet> derlenmiş <xref:System.Xml.Schema.XmlSchema> nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="bb274-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="bb274-119">Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bb274-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="bb274-120"><xref:System.Xml.Schema.XmlSchemaSimpleType> ve <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> sınıfları kullanarak `xs:string` basit tür kısıtlaması olan <xref:System.Xml.Schema.XmlSchemaElement> sınıfını kullanarak `PhoneNumber` öğesi oluşturur, kısıtlamanın <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> özelliğine bir model modeli ekler ve kısıtlamayı basit türün <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> özelliğine ve basit türe <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> öğesinin `PhoneNumber` ekler.</span><span class="sxs-lookup"><span data-stu-id="bb274-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>

4. <span data-ttu-id="bb274-121">Şema sonrası derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonunun <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> koleksiyonundaki her bir <xref:System.Xml.Schema.XmlSchemaElement> yineler.</span><span class="sxs-lookup"><span data-stu-id="bb274-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>

5. <span data-ttu-id="bb274-122">Öğesinin <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"Customer"`ise, <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfını ve <xref:System.Xml.Schema.XmlSchemaSequence> sınıfını kullanarak karmaşık türün sıra parçacığı kullanarak `Customer` öğenin karmaşık türünü alır.</span><span class="sxs-lookup"><span data-stu-id="bb274-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

6. <span data-ttu-id="bb274-123">Yeni `PhoneNumber` öğesini, sıranın ön derleme <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> koleksiyonunu kullanarak varolan `FirstName` ve `LastName` öğelerini içeren diziye ekler.</span><span class="sxs-lookup"><span data-stu-id="bb274-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>

7. <span data-ttu-id="bb274-124">Son olarak, <xref:System.Xml.Schema.XmlSchemaSet> sınıfının <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerini kullanarak değiştirilen <xref:System.Xml.Schema.XmlSchema> nesnesini yeniden işler ve derler ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="bb274-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="bb274-125">Aşağıda kodun tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb274-125">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

<span data-ttu-id="bb274-126">Aşağıda, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb274-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="xs:string" />
        <xs:element name="LastName" type="tns:LastNameType" />
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /
>
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

### <a name="title-attribute-example"></a><span data-ttu-id="bb274-127">Title özniteliği örneği</span><span class="sxs-lookup"><span data-stu-id="bb274-127">Title Attribute Example</span></span>

<span data-ttu-id="bb274-128">Bu ikinci kod örneği, müşteri şemasının `FirstName` öğesine yeni bir `Title` özniteliği ekler.</span><span class="sxs-lookup"><span data-stu-id="bb274-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="bb274-129">İlk kod örneğinde, `FirstName` öğenin türü `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="bb274-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="bb274-130">`FirstName` öğesinin dize içeriğiyle birlikte bir özniteliğe sahip olması için, türü basit bir içerik uzantısı içerik modeli olan karmaşık bir türe değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bb274-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>

<span data-ttu-id="bb274-131">Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.</span><span class="sxs-lookup"><span data-stu-id="bb274-131">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="bb274-132">Yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesine müşteri şemasını ekler ve sonra derler.</span><span class="sxs-lookup"><span data-stu-id="bb274-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="bb274-133">Şemayı okuma veya derleme ile karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilcisi tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="bb274-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="bb274-134"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini çağırarak <xref:System.Xml.Schema.XmlSchemaSet> derlenmiş <xref:System.Xml.Schema.XmlSchema> nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="bb274-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="bb274-135">Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bb274-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="bb274-136"><xref:System.Xml.Schema.XmlSchemaComplexType> sınıfını kullanarak `FirstName` öğesi için yeni bir karmaşık tür oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb274-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

4. <span data-ttu-id="bb274-137"><xref:System.Xml.Schema.XmlSchemaSimpleContent> ve <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> sınıfları kullanarak `xs:string`temel türünde yeni bir basit içerik uzantısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb274-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>

5. <span data-ttu-id="bb274-138">Yeni `Title` özniteliğini, bir `xs:string` <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> ve özniteliği basit içerik uzantısına ekleyen <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfını kullanarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb274-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>

6. <span data-ttu-id="bb274-139">Basit içeriğin içerik modelini basit içerik uzantısına ve karmaşık türün içerik modelini basit içeriğe ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb274-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>

7. <span data-ttu-id="bb274-140">Yeni karmaşık türü, şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="bb274-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

8. <span data-ttu-id="bb274-141">Şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonundaki her bir <xref:System.Xml.Schema.XmlSchemaObject> yineler.</span><span class="sxs-lookup"><span data-stu-id="bb274-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

> [!NOTE]
> <span data-ttu-id="bb274-142">`FirstName` öğesi şemada genel bir öğe olmadığından, <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonlarında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bb274-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="bb274-143">Kod örneği, önce `Customer` öğesini bularak `FirstName` öğesini konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="bb274-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>
>
> <span data-ttu-id="bb274-144">İlk kod örneği, şema-derleme sonrası <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu kullanılarak şemanın yerine geçen.</span><span class="sxs-lookup"><span data-stu-id="bb274-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="bb274-145">Bu örnekte, şemanın çapraz geçişini yapmak için şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb274-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="bb274-146">Her iki koleksiyon da şemadaki genel öğelere erişim sağlarken, şemadaki tüm genel öğeleri yinelemek ve herhangi bir PSCI özelliği olmaması gerektiğinden <xref:System.Xml.Schema.XmlSchema.Items%2A> koleksiyonunu yinelemek daha fazla zaman alır.</span><span class="sxs-lookup"><span data-stu-id="bb274-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="bb274-147">PSCI koleksiyonları (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>vb.), genel öğelerine, özniteliklerine ve türlerine ve bunların PSCı özelliklerine doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb274-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>

1. <span data-ttu-id="bb274-148"><xref:System.Xml.Schema.XmlSchemaObject>, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"Customer"`olan bir öğe ise, <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfını ve <xref:System.Xml.Schema.XmlSchemaSequence> sınıfını kullanarak karmaşık türdeki dizi parçacığı kullanarak `Customer` öğenin karmaşık türünü alır.</span><span class="sxs-lookup"><span data-stu-id="bb274-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

2. <span data-ttu-id="bb274-149">Şema öncesi derleme <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonundaki her bir <xref:System.Xml.Schema.XmlSchemaParticle> yineler.</span><span class="sxs-lookup"><span data-stu-id="bb274-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="bb274-150"><xref:System.Xml.Schema.XmlSchemaParticle> bir öğedir, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> kim `"FirstName"`, `FirstName` öğesinin <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> yeni `FirstName` karmaşık türe ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb274-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>

4. <span data-ttu-id="bb274-151">Son olarak, <xref:System.Xml.Schema.XmlSchemaSet> sınıfının <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerini kullanarak değiştirilen <xref:System.Xml.Schema.XmlSchema> nesnesini yeniden işler ve derler ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="bb274-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="bb274-152">Aşağıda kodun tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb274-152">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

<span data-ttu-id="bb274-153">Aşağıda, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb274-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
        <xs:element name="LastName" type="tns:LastNameType" />
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /
>
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="bb274-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb274-154">See also</span></span>

- [<span data-ttu-id="bb274-155">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bb274-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="bb274-156">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="bb274-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="bb274-157">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="bb274-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="bb274-158">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="bb274-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="bb274-159">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="bb274-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="bb274-160">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="bb274-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="bb274-161">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="bb274-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
