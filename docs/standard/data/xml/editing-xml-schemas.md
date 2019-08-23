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
ms.openlocfilehash: 3d0d67c82e753b044f759b4d1139c5f6b4837b31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948477"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="66cdd-102">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="66cdd-102">Editing XML Schemas</span></span>
<span data-ttu-id="66cdd-103">XML şeması düzenlenmesinin, şema nesne modeli 'nin (SOM) en önemli özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="66cdd-104">SOM 'un şema öncesi derleme özelliklerinin tümü bir XML şemasında varolan değerleri değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="66cdd-105">XML şeması daha sonra değişiklikleri yansıtacak şekilde yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="66cdd-106">SOM 'a yüklenen bir şemayı düzenlemenin ilk adımı şemanın gezedir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="66cdd-107">Bir şemayı düzenlemeye çalışmadan önce, SOM API 'sini kullanarak bir şemanın geçiş yapmaya alışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="66cdd-108">Şema-derleme-bilgi kümesi 'nin (PSCı) ön ve son şema-derleme özelliklerini de tanımanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="66cdd-109">XML şeması düzenleniyor</span><span class="sxs-lookup"><span data-stu-id="66cdd-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="66cdd-110">Bu bölümde, iki kod örneği sağlanır, ikisi de [derleme XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) içinde oluşturulan müşteri şemasını düzenler konu.</span><span class="sxs-lookup"><span data-stu-id="66cdd-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="66cdd-111">`PhoneNumber` İlk kod örneği, `Customer` öğesine yeni bir öğesi ekler ve ikinci kod örneği `FirstName` öğeye yeni `Title` bir öznitelik ekler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="66cdd-112">İlk örnek ayrıca, ikinci kod örneği şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonunu kullandığında, şema sonrası-derleme koleksiyonunu müşteri şemasına geçme yöntemi olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="66cdd-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="66cdd-113">PhoneNumber öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="66cdd-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="66cdd-114">Bu ilk kod örneği, müşteri şemasının `PhoneNumber` `Customer` öğesine yeni bir öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="66cdd-115">Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-115">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="66cdd-116">Müşteri şemasını yeni <xref:System.Xml.Schema.XmlSchemaSet> bir nesneye ekler ve bunu derler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="66cdd-117">Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilci tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="66cdd-118">Özelliği üzerinde <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchema> yineleerekderlenmişnesneyiöğesindenalır<xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="66cdd-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="66cdd-119">Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="66cdd-120"><xref:System.Xml.Schema.XmlSchemaElement> `xs:string` <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> , Ve sınıflarını<xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> kullanarak `PhoneNumber` basittürkısıtlamasıolansınıfınıkullanaraköğesioluşturur,kısıtlamanın<xref:System.Xml.Schema.XmlSchemaSimpleType> özelliğine bir model modeli ekler ve şunu ekler basit türün <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> özelliğine kısıtlama ve `PhoneNumber` öğenin basit türü. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A></span><span class="sxs-lookup"><span data-stu-id="66cdd-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4. <span data-ttu-id="66cdd-121">Şema sonrası derleme <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> koleksiyonu<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonundaki her birinin üzerinde dolaşır.</span><span class="sxs-lookup"><span data-stu-id="66cdd-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5. <span data-ttu-id="66cdd-122"><xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> Öğesi ise `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> <xref:System.Xml.Schema.XmlSchemaSequence> , sınıfını kullanarak ve karmaşık türün dizi partiküyi kullanarak öğenin karmaşık türünü alır. `"Customer"`</span><span class="sxs-lookup"><span data-stu-id="66cdd-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6. <span data-ttu-id="66cdd-123">Yeni `PhoneNumber` öğeyi, sıranın ön şema derlemesini <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kullanarak var olan `FirstName` ve `LastName` öğeleri içeren diziye ekler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7. <span data-ttu-id="66cdd-124">Son olarak <xref:System.Xml.Schema.XmlSchema> , değiştirilen nesneyi <xref:System.Xml.Schema.XmlSchemaSet> sınıfının <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerini kullanarak yeniden işler ve derler ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="66cdd-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="66cdd-125">Aşağıda kodun tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="66cdd-126">Aşağıda, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="66cdd-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
### <a name="title-attribute-example"></a><span data-ttu-id="66cdd-127">Title özniteliği örneği</span><span class="sxs-lookup"><span data-stu-id="66cdd-127">Title Attribute Example</span></span>  
 <span data-ttu-id="66cdd-128">Bu ikinci kod örneği, müşteri şemasının `Title` `FirstName` öğesine yeni bir öznitelik ekler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="66cdd-129">İlk kod örneğinde, `FirstName` `xs:string`öğesinin türü.</span><span class="sxs-lookup"><span data-stu-id="66cdd-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="66cdd-130">`FirstName` Öğesinin dize içeriğiyle birlikte bir özniteliğe sahip olması için, türü basit bir içerik uzantısı içerik modeli olan karmaşık bir türe değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="66cdd-131">Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-131">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="66cdd-132">Müşteri şemasını yeni <xref:System.Xml.Schema.XmlSchemaSet> bir nesneye ekler ve bunu derler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="66cdd-133">Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilci tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="66cdd-134">Özelliği üzerinde <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchema> yineleerekderlenmişnesneyiöğesindenalır<xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="66cdd-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="66cdd-135">Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="66cdd-136">Sınıfını kullanarak öğesi`FirstName` için yeni bir karmaşık tür oluşturur. <xref:System.Xml.Schema.XmlSchemaComplexType></span><span class="sxs-lookup"><span data-stu-id="66cdd-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4. <span data-ttu-id="66cdd-137">Ve<xref:System.Xml.Schema.XmlSchemaSimpleContent> `xs:string` sınıflarınıkullanaraktemeltürüileyenibirbasit<xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> içerik uzantısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66cdd-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5. <span data-ttu-id="66cdd-138">, ' A `Title` <xref:System.Xml.Schema.XmlSchemaAttribute> sahip<xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> sınıfınıkullanarakyeniözniteliğinioluştururveözniteliğinibasit`xs:string` içerik uzantısına ekler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6. <span data-ttu-id="66cdd-139">Basit içeriğin içerik modelini basit içerik uzantısına ve karmaşık türün içerik modelini basit içeriğe ayarlar.</span><span class="sxs-lookup"><span data-stu-id="66cdd-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7. <span data-ttu-id="66cdd-140">Yeni karmaşık türü, şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="66cdd-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8. <span data-ttu-id="66cdd-141">Şema öncesi derleme <xref:System.Xml.Schema.XmlSchemaObject> <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonundaki her birinin üzerinde yinelenir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66cdd-142">Öğe şemada genel bir öğe olmadığından, <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonlarda kullanılamaz. `FirstName`</span><span class="sxs-lookup"><span data-stu-id="66cdd-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="66cdd-143">Kod örneği, öğesini önce `FirstName` `Customer` öğesini bularak konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="66cdd-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="66cdd-144">İlk kod örneği, şema sonrası-derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu kullanılarak şemanın yerine geçen.</span><span class="sxs-lookup"><span data-stu-id="66cdd-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="66cdd-145">Bu örnekte, şemanın çapraz geçişini yapmak için şema öncesi <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> derleme koleksiyonu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66cdd-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="66cdd-146">Her iki koleksiyon de şemadaki genel öğelere erişim sağlarken, şemadaki tüm genel öğeleri yinelemek ve <xref:System.Xml.Schema.XmlSchema.Items%2A> herhangi bir psci özelliği olmaması gerektiğinden, koleksiyonda yineleme daha fazla zaman alır.</span><span class="sxs-lookup"><span data-stu-id="66cdd-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="66cdd-147">Psci koleksiyonları (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>vb.), genel öğelerine, özniteliklerine ve türlerine ve bunların pSCI özelliklerine doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="66cdd-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1. <span data-ttu-id="66cdd-148"><xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> <xref:System.Xml.Schema.XmlSchemaSequence> `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> Öğesi bir öğesi ise, sınıfını kullanarak sınıfı ve karmaşık türün dizi partiküyikullanaraköğeninkarmaşıktürünüalır.`"Customer"` <xref:System.Xml.Schema.XmlSchemaObject></span><span class="sxs-lookup"><span data-stu-id="66cdd-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2. <span data-ttu-id="66cdd-149">Şema öncesi derleme <xref:System.Xml.Schema.XmlSchemaParticle> <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonundaki her birinin üzerinde yinelenir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3. <span data-ttu-id="66cdd-150"><xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `FirstName` <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> Öğesi ise, kim`"FirstName"`ise, öğesinin öğesini Yeni`FirstName`karmaşıktüreayarlar. <xref:System.Xml.Schema.XmlSchemaParticle></span><span class="sxs-lookup"><span data-stu-id="66cdd-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4. <span data-ttu-id="66cdd-151">Son olarak <xref:System.Xml.Schema.XmlSchema> , değiştirilen nesneyi <xref:System.Xml.Schema.XmlSchemaSet> sınıfının <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerini kullanarak yeniden işler ve derler ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="66cdd-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="66cdd-152">Aşağıda kodun tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66cdd-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="66cdd-153">Aşağıda, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="66cdd-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66cdd-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66cdd-154">See also</span></span>

- [<span data-ttu-id="66cdd-155">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="66cdd-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="66cdd-156">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="66cdd-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="66cdd-157">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="66cdd-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="66cdd-158">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="66cdd-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="66cdd-159">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="66cdd-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="66cdd-160">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="66cdd-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="66cdd-161">Şema Derleme Sonrası Bilgi Kümesi</span><span class="sxs-lookup"><span data-stu-id="66cdd-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
