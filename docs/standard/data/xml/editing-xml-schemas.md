---
title: XML Şemalarını Düzenleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 119c4c13c90aeca8c14d2725d927c38be32212a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308724"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="53f3e-102">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="53f3e-102">Editing XML Schemas</span></span>
<span data-ttu-id="53f3e-103">Bir XML şeması düzenleme şema nesne modeli (SOM) en önemli özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="53f3e-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="53f3e-104">Tüm SOM öncesi schema derleme özelliklerini bir XML Şeması mevcut değerleri değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53f3e-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="53f3e-105">XML Şeması daha sonra bu değişiklikleri yansıtacak şekilde derlenebileceğini.</span><span class="sxs-lookup"><span data-stu-id="53f3e-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="53f3e-106">SOM yüklenen bir şema düzenleme ilk adımı, şema geçiş sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="53f3e-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="53f3e-107">Bir şema düzenleme girişiminde bulunmadan önce SOM API'sini kullanarak bir şema geçiş ile ilgili bilgi sahibi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="53f3e-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="53f3e-108">Öncesi ve sonrası schema derleme sonrası-schema-derleme-sonrası bilgi kümesi (PSCI) özellikleriyle ilgili bilgi sahibi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53f3e-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="53f3e-109">Bir XML şema düzenleme</span><span class="sxs-lookup"><span data-stu-id="53f3e-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="53f3e-110">Bu bölümde, iki kod örneği sağlanmıştır, ikisi de oluşturulan müşteri şemasını düzenleme [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="53f3e-111">İlk örnek kod yeni bir ekler `PhoneNumber` öğesine `Customer` öğesi ve ikinci kod örneğinde yeni bir ekler `Title` özniteliğini `FirstName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="53f3e-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="53f3e-112">İlk örnek de sonrası-schema-derleme kullanır <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonun ikinci kod örneğinde sırasında müşteri şema geçiş aracı olarak kullandığı öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="53f3e-113">PhoneNumber öğe örneği</span><span class="sxs-lookup"><span data-stu-id="53f3e-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="53f3e-114">Bu ilk kod örneğinde yeni bir ekler `PhoneNumber` öğesine `Customer` müşteri şema öğesi.</span><span class="sxs-lookup"><span data-stu-id="53f3e-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="53f3e-115">Kod örneği, aşağıdaki adımlarda, müşteri şema düzenler.</span><span class="sxs-lookup"><span data-stu-id="53f3e-115">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="53f3e-116">Yeni bir müşteri şema ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler.</span><span class="sxs-lookup"><span data-stu-id="53f3e-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="53f3e-117">Herhangi bir şema doğrulama uyarıları ve okuma veya şema derleme hatalarla karşılaşıldı işlenir <xref:System.Xml.Schema.ValidationEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="53f3e-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="53f3e-118">Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinden <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="53f3e-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="53f3e-119">Şema derlendiğinden sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özellikleri erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="53f3e-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="53f3e-120">Oluşturur `PhoneNumber` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaElement> sınıfı `xs:string` basit tür kısıtlama kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleType> ve <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> sınıflar, bir desen modeli ekler <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> kısıtlama özelliğini ekler kısıtlamaya <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> basit tür ve basit türü için özellik <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> , `PhoneNumber` öğesi.</span><span class="sxs-lookup"><span data-stu-id="53f3e-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4. <span data-ttu-id="53f3e-121">Her yinelenir <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> sonrası-schema-derleme koleksiyonu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5. <span data-ttu-id="53f3e-122">Varsa <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> öğesidir `"Customer"`, karmaşık türü alır `Customer` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53f3e-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6. <span data-ttu-id="53f3e-123">Yeni ekler `PhoneNumber` varolan içeren sıralı öğesine `FirstName` ve `LastName` öncesi-schema-derleme kullanarak öğeleri <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> dizisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7. <span data-ttu-id="53f3e-124">Son olarak, yeniden işler ve değiştirilmiş derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="53f3e-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="53f3e-125">Tam kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="53f3e-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="53f3e-126">Oluşturulan değiştirilmiş müşteri Şeması aşağıdaki gibidir [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
### <a name="title-attribute-example"></a><span data-ttu-id="53f3e-127">Başlık özniteliği örneği</span><span class="sxs-lookup"><span data-stu-id="53f3e-127">Title Attribute Example</span></span>  
 <span data-ttu-id="53f3e-128">Bu ikinci kod örneğinde yeni bir ekler `Title` özniteliğini `FirstName` müşteri şema öğesi.</span><span class="sxs-lookup"><span data-stu-id="53f3e-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="53f3e-129">İlk kod örneğinde, türü `FirstName` öğesi `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="53f3e-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="53f3e-130">İçin `FirstName` dize içerik türü değiştirildi, karmaşık bir türü basit içerik uzantısı içerik modeli ile birlikte bir öznitelik için öğesi.</span><span class="sxs-lookup"><span data-stu-id="53f3e-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="53f3e-131">Kod örneği, aşağıdaki adımlarda, müşteri şema düzenler.</span><span class="sxs-lookup"><span data-stu-id="53f3e-131">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="53f3e-132">Yeni bir müşteri şema ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler.</span><span class="sxs-lookup"><span data-stu-id="53f3e-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="53f3e-133">Herhangi bir şema doğrulama uyarıları ve okuma veya şema derleme hatalarla karşılaşıldı işlenir <xref:System.Xml.Schema.ValidationEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="53f3e-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="53f3e-134">Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinden <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="53f3e-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="53f3e-135">Şema derlendiğinden sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özellikleri erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="53f3e-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="53f3e-136">İçin yeni bir karmaşık türü oluşturur `FirstName` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53f3e-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4. <span data-ttu-id="53f3e-137">Taban bir türü ile bir yeni basit içerik uzantısı oluşturur `xs:string`kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleContent> ve <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="53f3e-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5. <span data-ttu-id="53f3e-138">Yeni oluşturur `Title` kullanarak özniteliği <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfı ile bir <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> , `xs:string` ve öznitelik basit içerik uzantısı ekler.</span><span class="sxs-lookup"><span data-stu-id="53f3e-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6. <span data-ttu-id="53f3e-139">Basit içeriğin içerik modeli, basit içerik uzantı ve karmaşık türün basit içerik için içerik modeli için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="53f3e-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7. <span data-ttu-id="53f3e-140">Yeni karmaşık tür öncesi-schema-derlemeye ekler <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8. <span data-ttu-id="53f3e-141">Her yinelenir <xref:System.Xml.Schema.XmlSchemaObject> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53f3e-142">Çünkü `FirstName` öğesi genel bir şema öğesi değil, mevcut değildir <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="53f3e-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="53f3e-143">Kod örneği bulur `FirstName` ilk bulma tarafından öğesi `Customer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="53f3e-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="53f3e-144">İlk örnek kod geçiş sonrası-schema-derleme kullanarak şemasını <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="53f3e-145">Bu örnekte, öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> toplama şema geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53f3e-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="53f3e-146">Her iki koleksiyon şema genel öğelere erişim sunarken, üzerinden yineleme <xref:System.Xml.Schema.XmlSchema.Items%2A> koleksiyonu olduğundan daha uzun süren şemadaki tüm genel öğeler üzerinde yinelenmelidir ve herhangi bir PSCI özelliği yok.</span><span class="sxs-lookup"><span data-stu-id="53f3e-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="53f3e-147">PSCI koleksiyonları (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, vb.) kendi genel öğeler, öznitelikler ve türler ve PSCI özelliklerini doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="53f3e-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1. <span data-ttu-id="53f3e-148">Varsa <xref:System.Xml.Schema.XmlSchemaObject> bir öğedir, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olduğu `"Customer"`, karmaşık türü alır `Customer` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53f3e-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2. <span data-ttu-id="53f3e-149">Her yinelenir <xref:System.Xml.Schema.XmlSchemaParticle> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3. <span data-ttu-id="53f3e-150">Varsa <xref:System.Xml.Schema.XmlSchemaParticle> bir öğedir kullanan kişinin <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olduğu `"FirstName"`, ayarlar <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> , `FirstName` yeni öğe `FirstName` karmaşık tür.</span><span class="sxs-lookup"><span data-stu-id="53f3e-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4. <span data-ttu-id="53f3e-151">Son olarak, yeniden işler ve değiştirilmiş derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="53f3e-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="53f3e-152">Tam kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="53f3e-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="53f3e-153">Oluşturulan değiştirilmiş müşteri Şeması aşağıdaki gibidir [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.</span><span class="sxs-lookup"><span data-stu-id="53f3e-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53f3e-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53f3e-154">See also</span></span>

- [<span data-ttu-id="53f3e-155">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="53f3e-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="53f3e-156">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="53f3e-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="53f3e-157">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="53f3e-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="53f3e-158">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="53f3e-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="53f3e-159">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="53f3e-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="53f3e-160">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="53f3e-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="53f3e-161">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="53f3e-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
