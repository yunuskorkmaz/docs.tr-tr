---
description: 'Daha fazla bilgi edinin: XML şemaları düzenleniyor'
title: XML Şemalarını Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: 19f757f537281b16d30dfc831e0dc8f0f4735987
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783345"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="6633b-103">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="6633b-103">Editing XML Schemas</span></span>

<span data-ttu-id="6633b-104">XML şeması düzenlenmesinin, şema nesne modeli 'nin (SOM) en önemli özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="6633b-104">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="6633b-105">SOM 'un şema öncesi derleme özelliklerinin tümü bir XML şemasında varolan değerleri değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6633b-105">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="6633b-106">XML şeması daha sonra değişiklikleri yansıtacak şekilde yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="6633b-106">The XML schema can then be recompiled to reflect the changes.</span></span>

<span data-ttu-id="6633b-107">SOM 'a yüklenen bir şemayı düzenlemenin ilk adımı şemanın gezedir.</span><span class="sxs-lookup"><span data-stu-id="6633b-107">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="6633b-108">Bir şemayı düzenlemeye çalışmadan önce, SOM API 'sini kullanarak bir şemanın geçiş yapmaya alışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6633b-108">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="6633b-109">Şema-derleme-bilgi kümesi 'nin (PSCı) ön ve son şema-derleme özelliklerini de tanımanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6633b-109">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>

## <a name="editing-an-xml-schema"></a><span data-ttu-id="6633b-110">XML şeması düzenleniyor</span><span class="sxs-lookup"><span data-stu-id="6633b-110">Editing an XML Schema</span></span>

<span data-ttu-id="6633b-111">Bu bölümde, iki kod örneği sağlanır, ikisi de [derleme XML şemaları](building-xml-schemas.md) içinde oluşturulan müşteri şemasını düzenler konu.</span><span class="sxs-lookup"><span data-stu-id="6633b-111">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span> <span data-ttu-id="6633b-112">İlk kod örneği, öğesine yeni bir `PhoneNumber` öğesi ekler `Customer` ve ikinci kod örneği öğeye yeni bir `Title` öznitelik ekler `FirstName` .</span><span class="sxs-lookup"><span data-stu-id="6633b-112">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="6633b-113">İlk örnek ayrıca, <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> İkinci kod örneği şema öncesi derleme koleksiyonunu kullandığında, şema sonrası-derleme koleksiyonunu müşteri şemasına geçme yöntemi olarak kullanır <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6633b-113">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

### <a name="phonenumber-element-example"></a><span data-ttu-id="6633b-114">PhoneNumber öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="6633b-114">PhoneNumber Element Example</span></span>

<span data-ttu-id="6633b-115">Bu ilk kod örneği, `PhoneNumber` Müşteri şemasının öğesine yeni bir öğesi ekler `Customer` .</span><span class="sxs-lookup"><span data-stu-id="6633b-115">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="6633b-116">Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.</span><span class="sxs-lookup"><span data-stu-id="6633b-116">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="6633b-117">Müşteri şemasını yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesneye ekler ve bunu derler.</span><span class="sxs-lookup"><span data-stu-id="6633b-117">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="6633b-118">Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları temsilci tarafından işlenir <xref:System.Xml.Schema.ValidationEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="6633b-118">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="6633b-119"><xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> Özelliği üzerinde yineleerek derlenmiş nesneyi öğesinden alır <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="6633b-119">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="6633b-120">Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6633b-120">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="6633b-121">, `PhoneNumber` <xref:System.Xml.Schema.XmlSchemaElement> `xs:string` Ve sınıflarını kullanarak basit tür kısıtlaması olan sınıfını kullanarak öğesi oluşturur <xref:System.Xml.Schema.XmlSchemaSimpleType> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> , kısıtlamanın özelliğine bir model modeli ekler <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> ve kısıtlama, <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> basit türdeki ve basit tür özelliğine öğesi öğesine eklenir <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> `PhoneNumber` .</span><span class="sxs-lookup"><span data-stu-id="6633b-121">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>

4. <span data-ttu-id="6633b-122"><xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> Şema sonrası derleme koleksiyonu koleksiyonundaki her birinin üzerinde dolaşır <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6633b-122">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>

5. <span data-ttu-id="6633b-123">Öğesi ise, sınıfını kullanarak <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"Customer"` `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> ve karmaşık türün dizi partiküyi kullanarak öğenin karmaşık türünü alır <xref:System.Xml.Schema.XmlSchemaSequence> .</span><span class="sxs-lookup"><span data-stu-id="6633b-123">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

6. <span data-ttu-id="6633b-124">Yeni öğeyi, `PhoneNumber` `FirstName` `LastName` sıranın ön şema derlemesini kullanarak var olan ve öğeleri içeren diziye ekler <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> .</span><span class="sxs-lookup"><span data-stu-id="6633b-124">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>

7. <span data-ttu-id="6633b-125">Son olarak, değiştirilen <xref:System.Xml.Schema.XmlSchema> nesneyi sınıfının ve yöntemlerini kullanarak yeniden işler ve derler ve <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="6633b-125">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="6633b-126">Aşağıda kodun tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6633b-126">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

<span data-ttu-id="6633b-127">Aşağıda, [XML şemaları oluşturma](building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6633b-127">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

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

### <a name="title-attribute-example"></a><span data-ttu-id="6633b-128">Title özniteliği örneği</span><span class="sxs-lookup"><span data-stu-id="6633b-128">Title Attribute Example</span></span>

<span data-ttu-id="6633b-129">Bu ikinci kod örneği, `Title` Müşteri şemasının öğesine yeni bir öznitelik ekler `FirstName` .</span><span class="sxs-lookup"><span data-stu-id="6633b-129">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="6633b-130">İlk kod örneğinde, `FirstName` öğesinin türü `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="6633b-130">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="6633b-131">`FirstName`Öğesinin dize içeriğiyle birlikte bir özniteliğe sahip olması için, türü basit bir içerik uzantısı içerik modeli olan karmaşık bir türe değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6633b-131">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>

<span data-ttu-id="6633b-132">Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.</span><span class="sxs-lookup"><span data-stu-id="6633b-132">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="6633b-133">Müşteri şemasını yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesneye ekler ve bunu derler.</span><span class="sxs-lookup"><span data-stu-id="6633b-133">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="6633b-134">Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları temsilci tarafından işlenir <xref:System.Xml.Schema.ValidationEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="6633b-134">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="6633b-135"><xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> Özelliği üzerinde yineleerek derlenmiş nesneyi öğesinden alır <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="6633b-135">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="6633b-136">Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6633b-136">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="6633b-137">Sınıfını kullanarak öğesi için yeni bir karmaşık tür oluşturur `FirstName` <xref:System.Xml.Schema.XmlSchemaComplexType> .</span><span class="sxs-lookup"><span data-stu-id="6633b-137">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

4. <span data-ttu-id="6633b-138">`xs:string`Ve sınıflarını kullanarak temel türü ile yeni bir basit içerik uzantısı oluşturur <xref:System.Xml.Schema.XmlSchemaSimpleContent> <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> .</span><span class="sxs-lookup"><span data-stu-id="6633b-138">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>

5. <span data-ttu-id="6633b-139">, `Title` <xref:System.Xml.Schema.XmlSchemaAttribute> ' A sahip sınıfını kullanarak yeni özniteliğini oluşturur <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> `xs:string` ve özniteliğini basit içerik uzantısına ekler.</span><span class="sxs-lookup"><span data-stu-id="6633b-139">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>

6. <span data-ttu-id="6633b-140">Basit içeriğin içerik modelini basit içerik uzantısına ve karmaşık türün içerik modelini basit içeriğe ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6633b-140">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>

7. <span data-ttu-id="6633b-141">Yeni karmaşık türü, şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="6633b-141">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

8. <span data-ttu-id="6633b-142"><xref:System.Xml.Schema.XmlSchemaObject>Şema öncesi derleme koleksiyonundaki her birinin üzerinde yinelenir <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6633b-142">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

> [!NOTE]
> <span data-ttu-id="6633b-143">`FirstName`Öğe şemada genel bir öğe olmadığından, <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonlarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6633b-143">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="6633b-144">Kod örneği, öğesini `FirstName` önce öğesini bularak konumlandırır `Customer` .</span><span class="sxs-lookup"><span data-stu-id="6633b-144">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>
>
> <span data-ttu-id="6633b-145">İlk kod örneği, şema sonrası-derleme koleksiyonu kullanılarak şemanın yerine geçen <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6633b-145">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="6633b-146">Bu örnekte, <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> şemanın çapraz geçişini yapmak için şema öncesi derleme koleksiyonu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6633b-146">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="6633b-147">Her iki koleksiyon de şemadaki genel öğelere erişim sağlarken, <xref:System.Xml.Schema.XmlSchema.Items%2A> şemadaki tüm genel öğeleri yinelemek ve herhangi BIR PSCI özelliği olmaması gerektiğinden, koleksiyonda yineleme daha fazla zaman alır.</span><span class="sxs-lookup"><span data-stu-id="6633b-147">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="6633b-148">Psci koleksiyonları ( <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> , <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType> , vb <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType> .), genel öğelerine, özniteliklerine ve türlerine ve bunların pSCI özelliklerine doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6633b-148">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>

1. <span data-ttu-id="6633b-149"><xref:System.Xml.Schema.XmlSchemaObject>Öğesi bir öğesi ise, sınıfını kullanarak <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"Customer"` `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve karmaşık türün dizi partiküyi kullanarak öğenin karmaşık türünü alır <xref:System.Xml.Schema.XmlSchemaSequence> .</span><span class="sxs-lookup"><span data-stu-id="6633b-149">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

2. <span data-ttu-id="6633b-150"><xref:System.Xml.Schema.XmlSchemaParticle>Şema öncesi derleme koleksiyonundaki her birinin üzerinde yinelenir <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6633b-150">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="6633b-151">Öğesi ise <xref:System.Xml.Schema.XmlSchemaParticle> , kim ise, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"FirstName"` <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> `FirstName` öğesinin öğesini yeni `FirstName` karmaşık türe ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6633b-151">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>

4. <span data-ttu-id="6633b-152">Son olarak, değiştirilen <xref:System.Xml.Schema.XmlSchema> nesneyi sınıfının ve yöntemlerini kullanarak yeniden işler ve derler ve <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="6633b-152">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="6633b-153">Aşağıda kodun tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6633b-153">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

<span data-ttu-id="6633b-154">Aşağıda, [XML şemaları oluşturma](building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6633b-154">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
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
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="6633b-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6633b-155">See also</span></span>

- [<span data-ttu-id="6633b-156">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6633b-156">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="6633b-157">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="6633b-157">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="6633b-158">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="6633b-158">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="6633b-159">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="6633b-159">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="6633b-160">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="6633b-160">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="6633b-161">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="6633b-161">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="6633b-162">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="6633b-162">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
