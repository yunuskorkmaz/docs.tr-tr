---
title: "XML şemaları düzenleme"
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
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9505f60b2000ef227463404dab051ecb7fa3cc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="0f095-102">XML şemaları düzenleme</span><span class="sxs-lookup"><span data-stu-id="0f095-102">Editing XML Schemas</span></span>
<span data-ttu-id="0f095-103">Bir XML şeması düzenleme şema nesne modeli (SOM) en önemli özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="0f095-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="0f095-104">Tüm SOM öncesi schema derleme özelliklerinin bir XML şeması var olan değerleri değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f095-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="0f095-105">XML şema değişiklikleri yansıtacak şekilde sonra derlenebileceğini.</span><span class="sxs-lookup"><span data-stu-id="0f095-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="0f095-106">SOM yüklenen bir şema düzenleme ilk şema gezinmesine adımdır.</span><span class="sxs-lookup"><span data-stu-id="0f095-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="0f095-107">Bir şema düzenlemeyi denemeden önce SOM API kullanarak bir şema geçiş ile biliyor olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f095-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="0f095-108">Sonrası-schema-derleme-bilgi (PSCI) öncesi ve sonrası schema derleme özellikleriyle tanıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f095-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="0f095-109">Bir XML şeması düzenleme</span><span class="sxs-lookup"><span data-stu-id="0f095-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="0f095-110">Bu bölümde, iki kod örnekleri sağlanır, her ikisi de oluşturulan müşteri şema düzenleme [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.</span><span class="sxs-lookup"><span data-stu-id="0f095-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="0f095-111">İlk örnek kod yeni bir ekler `PhoneNumber` öğesine `Customer` öğesi ikinci kod örneği ekler ve yeni bir `Title` özniteliğini `FirstName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0f095-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="0f095-112">İlk örnek de sonrası-schema-derleme kullanır <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu ikinci kod örneğinde sırasında müşteri şeması geçiş aracı olarak kullanır öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0f095-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="0f095-113">PhoneNumber öğe örneği</span><span class="sxs-lookup"><span data-stu-id="0f095-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="0f095-114">Bu ilk örnek kod yeni bir ekler `PhoneNumber` öğesine `Customer` müşteri şemasının öğesidir.</span><span class="sxs-lookup"><span data-stu-id="0f095-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="0f095-115">Kod örneği, aşağıdaki adımlarda müşteri şeması düzenler.</span><span class="sxs-lookup"><span data-stu-id="0f095-115">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="0f095-116">Müşteri şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler.</span><span class="sxs-lookup"><span data-stu-id="0f095-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="0f095-117">Şema doğrulama uyarıları ve okuma veya şema derleme karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="0f095-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="0f095-118">Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0f095-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="0f095-119">Sonrası-Schema-derleme-bilgi (PSCI) özellikleri, şema derlendiğinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f095-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="0f095-120">Oluşturur `PhoneNumber` öğesi kullanılarak <xref:System.Xml.Schema.XmlSchemaElement> sınıfı, `xs:string` basit tür kısıtlama kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleType> ve <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> sınıfları, bir desen modeli ekler <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> kısıtlama özelliğini ve ekler kısıtlama için <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> basit tür ve basit tür özelliği <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> , `PhoneNumber` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0f095-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4.  <span data-ttu-id="0f095-121">Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> sonrası-schema-derleme koleksiyonu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0f095-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5.  <span data-ttu-id="0f095-122">Varsa <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> öğesidir `"Customer"`, karmaşık türü alır `Customer` öğesi kullanılarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f095-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6.  <span data-ttu-id="0f095-123">Yeni ekler `PhoneNumber` varolan içeren sırası öğesine `FirstName` ve `LastName` öncesi-schema-derleme kullanarak öğeleri <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> dizisi topluluğu.</span><span class="sxs-lookup"><span data-stu-id="0f095-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7.  <span data-ttu-id="0f095-124">Son olarak, yeniden işler ve değiştirilen derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="0f095-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="0f095-125">Tam kod örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0f095-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="0f095-126">Oluşturulan değiştirilmiş müşteri şeması aşağıdadır [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.</span><span class="sxs-lookup"><span data-stu-id="0f095-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
### <a name="title-attribute-example"></a><span data-ttu-id="0f095-127">Başlık özniteliği örneği</span><span class="sxs-lookup"><span data-stu-id="0f095-127">Title Attribute Example</span></span>  
 <span data-ttu-id="0f095-128">İkinci Bu kod örneği, yeni bir ekler `Title` özniteliğini `FirstName` müşteri şemasının öğesidir.</span><span class="sxs-lookup"><span data-stu-id="0f095-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="0f095-129">İlk kod örneğinde, türü `FirstName` öğesi `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="0f095-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="0f095-130">İçin `FirstName` dize içerik türü değişti, karmaşık türü bir basit içerik uzantısı içerik modeli ile birlikte bir özniteliği olan öğe.</span><span class="sxs-lookup"><span data-stu-id="0f095-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="0f095-131">Kod örneği, aşağıdaki adımlarda müşteri şeması düzenler.</span><span class="sxs-lookup"><span data-stu-id="0f095-131">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="0f095-132">Müşteri şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler.</span><span class="sxs-lookup"><span data-stu-id="0f095-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="0f095-133">Şema doğrulama uyarıları ve okuma veya şema derleme karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="0f095-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="0f095-134">Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0f095-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="0f095-135">Sonrası-Schema-derleme-bilgi (PSCI) özellikleri, şema derlendiğinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f095-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="0f095-136">Yeni karmaşık tür için oluşturur `FirstName` öğesi kullanılarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f095-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4.  <span data-ttu-id="0f095-137">Yeni basit içerik uzantısı, temel bir tür ile oluşturur `xs:string`kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleContent> ve <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="0f095-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5.  <span data-ttu-id="0f095-138">Yeni oluşturur `Title` kullanarak öznitelik <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfı ile bir <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> , `xs:string` ve öznitelik basit içerik uzantısı ekler.</span><span class="sxs-lookup"><span data-stu-id="0f095-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6.  <span data-ttu-id="0f095-139">Basit içerik uzantısı ve basit içeriğe karmaşık türünün içerik modeli için basit içerik içerik modeli ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f095-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7.  <span data-ttu-id="0f095-140">Yeni karmaşık tür öncesi-schema-derlemeye ekler <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0f095-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8.  <span data-ttu-id="0f095-141">Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaObject> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0f095-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f095-142">Çünkü `FirstName` öğesi şemada genel öğesi değil, kullanılabilir değil <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="0f095-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="0f095-143">Kod örneği bulur `FirstName` ilk bulma tarafından öğesi `Customer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0f095-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="0f095-144">İlk örnek kod sonrası-schema-derleme kullanarak şemasını geçiş <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0f095-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="0f095-145">Bu örnekte, öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> toplama şema çapraz geçiş için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f095-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="0f095-146">Her iki koleksiyon şemada genel öğelere erişim sunarken üzerinden yineleme <xref:System.Xml.Schema.XmlSchema.Items%2A> koleksiyonu olduğundan daha uzun süren şemadaki tüm genel öğeler üzerinden yineleme gerekir ve herhangi bir PSCI özellik yok.</span><span class="sxs-lookup"><span data-stu-id="0f095-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="0f095-147">PSCI koleksiyonları (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, vb.) genel öğeleri, öznitelikleri ve türleri ve bunların PSCI özelliklerini doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f095-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1.  <span data-ttu-id="0f095-148">Varsa <xref:System.Xml.Schema.XmlSchemaObject> bir öğe olan <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olan `"Customer"`, karmaşık türü alır `Customer` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f095-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2.  <span data-ttu-id="0f095-149">Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaParticle> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0f095-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="0f095-150">Varsa <xref:System.Xml.Schema.XmlSchemaParticle> bir öğe kimin 's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olan `"FirstName"`, ayarlar <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> , `FirstName` yeni öğesine `FirstName` karmaşık tür.</span><span class="sxs-lookup"><span data-stu-id="0f095-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4.  <span data-ttu-id="0f095-151">Son olarak, yeniden işler ve değiştirilen derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="0f095-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="0f095-152">Tam kod örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0f095-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="0f095-153">Oluşturulan değiştirilmiş müşteri şeması aşağıdadır [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.</span><span class="sxs-lookup"><span data-stu-id="0f095-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f095-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f095-154">See Also</span></span>  
 [<span data-ttu-id="0f095-155">XML şema nesne modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="0f095-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="0f095-156">Okuma ve yazma XML şemaları</span><span class="sxs-lookup"><span data-stu-id="0f095-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="0f095-157">Yapı XML şemaları</span><span class="sxs-lookup"><span data-stu-id="0f095-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="0f095-158">XML şemaları çapraz geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="0f095-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="0f095-159">Dahil olmak üzere veya XML şemalarını içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="0f095-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="0f095-160">Şema derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="0f095-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="0f095-161">Derleme sonrası şema bilgi</span><span class="sxs-lookup"><span data-stu-id="0f095-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
