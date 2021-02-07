---
description: 'Daha fazla bilgi edinin: XML belgelerinden şemaları erteleme'
title: XML Belgelerinden Şema Çıkarımı Yapma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: b8a064e0612293ee2990ec8acc3cc4b5f0b32054
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713656"
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="46b16-103">XML Belgelerinden Şema Çıkarımı Yapma</span><span class="sxs-lookup"><span data-stu-id="46b16-103">Inferring Schemas from XML Documents</span></span>

<span data-ttu-id="46b16-104">Bu konuda, sınıfının bir XML <xref:System.Xml.Schema.XmlSchemaInference> belgesi yapısından BIR XML şeması tanım dili (xsd) şeması çıkarması için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46b16-104">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="46b16-105">Şema çıkarımı Işlemi</span><span class="sxs-lookup"><span data-stu-id="46b16-105">The Schema Inference Process</span></span>  

 <span data-ttu-id="46b16-106"><xref:System.Xml.Schema.XmlSchemaInference>Ad alanı sınıfı, <xref:System.Xml.Schema?displayProperty=nameWithType> bir XML belgesi yapısından bir veya daha fazla XML şeması tanım DILI (xsd) şeması oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46b16-106">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="46b16-107">Oluşturulan şemalar özgün XML belgesini doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46b16-107">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="46b16-108">Sınıfı tarafından bir XML belgesi işlendiği için <xref:System.Xml.Schema.XmlSchemaInference> , <xref:System.Xml.Schema.XmlSchemaInference> sınıfı XML belgesindeki öğeleri ve öznitelikleri tanımlayan şema bileşenleriyle ilgili varsayımlar yapar.</span><span class="sxs-lookup"><span data-stu-id="46b16-108">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="46b16-109"><xref:System.Xml.Schema.XmlSchemaInference>Sınıfı, belirli bir öğe veya öznitelik için en kısıtlayıcı türü azaltarak, şema bileşenlerini kısıtlanmış bir şekilde de algılar.</span><span class="sxs-lookup"><span data-stu-id="46b16-109">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="46b16-110">XML belgesi hakkında daha fazla bilgi toplandığından, bu kısıtlamalar daha az kısıtlayıcı olan türleri azaltarak gevşur.</span><span class="sxs-lookup"><span data-stu-id="46b16-110">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="46b16-111">Çıkarsanan en az kısıtlayıcı tür `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="46b16-111">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="46b16-112">Örneğin, bir XML belgesinin aşağıdaki parçasını alın.</span><span class="sxs-lookup"><span data-stu-id="46b16-112">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 <span data-ttu-id="46b16-113">Yukarıdaki örnekte, `attribute1` özniteliğe işlem tarafından bir değer ile karşılaşıldığında `6` <xref:System.Xml.Schema.XmlSchemaInference> , türünde olduğu varsayılır `xs:unsignedByte` .</span><span class="sxs-lookup"><span data-stu-id="46b16-113">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="46b16-114">`parent`İşlem tarafından ikinci öğe ile karşılaşıldığında <xref:System.Xml.Schema.XmlSchemaInference> , `xs:string` özniteliğinin değeri artık olduğundan, kısıtlama, türü olarak değiştirilerek gevşerek yapılır `attribute1` `A` .</span><span class="sxs-lookup"><span data-stu-id="46b16-114">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="46b16-115">Benzer şekilde, `minOccurs` `child` şemada çıkarılan tüm öğelerin özniteliği, `minOccurs="0"` ikinci üst öğenin alt öğeleri olmadığından, öğesine gevşulmuş olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="46b16-115">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="46b16-116">XML Belgelerinden Şema Çıkarımı Yapma</span><span class="sxs-lookup"><span data-stu-id="46b16-116">Inferring Schemas from XML Documents</span></span>  

 <span data-ttu-id="46b16-117"><xref:System.Xml.Schema.XmlSchemaInference>Sınıfı BIR <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> XML belgesinden şemayı çıkarsmak için iki aşırı yüklenmiş yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="46b16-117">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="46b16-118">İlk yöntem, bir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> XML belgesini temel alan bir şema oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46b16-118">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="46b16-119">İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem, birden çok XML belgesini açıklayan bir şemayı çıkarmakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46b16-119">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="46b16-120">Örneğin, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> tüm XML belgesi kümesini açıklayan bir şema oluşturmak için birden çok XML belgesini tek seferde bir kez akışa aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46b16-120">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="46b16-121">İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem bir nesne içindeki BIR XML belgesinden şemayı içerir <xref:System.Xml.XmlReader> ve <xref:System.Xml.Schema.XmlSchemaSet> çıkarılan şemayı içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="46b16-121">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="46b16-122">İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem, <xref:System.Xml.Schema.XmlSchemaSet> NESNESINDE bulunan XML belgesiyle aynı hedef ad alanına sahip bir şema için bir nesne arar <xref:System.Xml.XmlReader> , varolan şemayı iyileştirir ve <xref:System.Xml.Schema.XmlSchemaSet> çıkarılan şemayı içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="46b16-122">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="46b16-123">İyileştirilmiş şemada yapılan değişiklikler XML belgesinde bulunan yeni yapıyı temel alır.</span><span class="sxs-lookup"><span data-stu-id="46b16-123">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="46b16-124">Örneğin, bir XML belgesi çapraz yapıldıkça, bulunan veri türleri hakkında varsayımlar yapılır ve şema bu varsayımlar temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="46b16-124">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="46b16-125">Ancak, özgün varsayıma göre farklılık gösteren ikinci bir çıkarım geçişinde veriye karşılaşılırsa, şema iyileştirilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46b16-125">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="46b16-126">Aşağıdaki örnek, iyileştirme sürecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46b16-126">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="46b16-127">Örnek, `item1.xml` ilk girişi olarak aşağıdaki dosyayı alır.</span><span class="sxs-lookup"><span data-stu-id="46b16-127">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="46b16-128">Örnek, `item2.xml` dosyayı ikinci girdi olarak alır:</span><span class="sxs-lookup"><span data-stu-id="46b16-128">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="46b16-129">`productID`Ilk XML belgesinde özniteliğiyle karşılaşıldığında, değerinin `123456789` bir tür olduğu varsayılır `xs:unsignedInt` .</span><span class="sxs-lookup"><span data-stu-id="46b16-129">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="46b16-130">Ancak, ikinci XML belgesi okunmadıysa ve değeri `A53-246` bulunursa, `xs:unsignedInt` tür artık kabul edilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="46b16-130">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="46b16-131">Şema iyileştirilmektedir ve türü `productID` olarak değişir `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="46b16-131">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="46b16-132">Ayrıca, `minOccurs` öğesi için özniteliği olarak `supplierID` ayarlanır `0` , çünkü ikinci XML belgesi hiç `supplierID` öğe içermiyor.</span><span class="sxs-lookup"><span data-stu-id="46b16-132">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="46b16-133">İlk XML belgesinden çıkarılan şema aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46b16-133">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="46b16-134">Aşağıda, birinci XML belgesinden çıkarılan ve ikinci XML belgesi tarafından iyileştirilmiş şema verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46b16-134">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="46b16-135">Satır içi şemalar</span><span class="sxs-lookup"><span data-stu-id="46b16-135">Inline Schemas</span></span>  

 <span data-ttu-id="46b16-136">İşlem sırasında satır içi bir XML şeması tanım dili (XSD) şemasına karşılaşılırsa <xref:System.Xml.Schema.XmlSchemaInference> , bir oluşturulur <xref:System.Xml.Schema.XmlSchemaInferenceException> .</span><span class="sxs-lookup"><span data-stu-id="46b16-136">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="46b16-137">Örneğin, aşağıdaki satır içi şema bir oluşturur <xref:System.Xml.Schema.XmlSchemaInferenceException> .</span><span class="sxs-lookup"><span data-stu-id="46b16-137">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="46b16-138">Iyileştirilelemez şemalar</span><span class="sxs-lookup"><span data-stu-id="46b16-138">Schemas that Cannot be Refined</span></span>  

 <span data-ttu-id="46b16-139">XML şeması tanım dili (XSD) şema <xref:System.Xml.Schema.XmlSchemaInference> işleminin, daraltmak için bir tür verildiyse ve bir özel durumun oluşturulmasına neden olması halinde işleyememesi gereken W3C xml şema yapıları vardır.</span><span class="sxs-lookup"><span data-stu-id="46b16-139">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="46b16-140">Üst düzey kompozisyonu bir sıra dışında herhangi bir şey olan karmaşık bir tür gibi.</span><span class="sxs-lookup"><span data-stu-id="46b16-140">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="46b16-141">Şema nesne modelinde (SOM), bu bir <xref:System.Xml.Schema.XmlSchemaComplexType> <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> özelliği bir örneği olmayan öğesine karşılık gelir <xref:System.Xml.Schema.XmlSchemaSequence> .</span><span class="sxs-lookup"><span data-stu-id="46b16-141">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b16-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46b16-142">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="46b16-143">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="46b16-143">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="46b16-144">XML Şemasından Çıkarım Yapma</span><span class="sxs-lookup"><span data-stu-id="46b16-144">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="46b16-145">Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları</span><span class="sxs-lookup"><span data-stu-id="46b16-145">Rules for Inferring Schema Node Types and Structure</span></span>](rules-for-inferring-schema-node-types-and-structure.md)
- [<span data-ttu-id="46b16-146">Basit Türlerin Çıkarımını Yapma Kuralları</span><span class="sxs-lookup"><span data-stu-id="46b16-146">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
