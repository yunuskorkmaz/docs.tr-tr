---
title: "XML belgelerden şemaları çıkarımını yapma"
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
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aa4d6d2758392fc48969b08db30b91bdfe0eeaa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="541f5-102">XML belgelerden şemaları çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="541f5-102">Inferring Schemas from XML Documents</span></span>
<span data-ttu-id="541f5-103">Bu konuda nasıl kullanılacağını açıklar <xref:System.Xml.Schema.XmlSchemaInference> bir XML belgesi yapısını bir XML Şeması Tanım Dili (XSD) şemadan gerçekleştirip sınıfı.</span><span class="sxs-lookup"><span data-stu-id="541f5-103">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="541f5-104">Şema çıkarım işlemi</span><span class="sxs-lookup"><span data-stu-id="541f5-104">The Schema Inference Process</span></span>  
 <span data-ttu-id="541f5-105"><xref:System.Xml.Schema.XmlSchemaInference> Sınıfının <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı, bir veya daha fazla XML Şeması Tanım Dili (XSD) şemaları bir XML belgesi yapısından oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="541f5-105">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="541f5-106">Oluşturulan şemaları, özgün XML belgesi doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="541f5-106">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="541f5-107">Bir XML olarak belge tarafından işlenen <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, <xref:System.Xml.Schema.XmlSchemaInference> sınıfı öğeleri ve öznitelikleri XML belgesindeki açıklayan şema bileşenleri hakkında varsayımlar yapar.</span><span class="sxs-lookup"><span data-stu-id="541f5-107">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="541f5-108"><xref:System.Xml.Schema.XmlSchemaInference> Sınıfı ayrıca oluşturur şema bileşenleri kısıtlanmış bir şekilde belirli öğesi veya özniteliği için en kısıtlayıcı türü çıkarımını yapma.</span><span class="sxs-lookup"><span data-stu-id="541f5-108">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="541f5-109">XML belgesi hakkında daha fazla bilgi toplanan gibi bu kısıtlamaların daha az kısıtlayıcı türlerinin çıkarımını yapma gevşetiliyormuş.</span><span class="sxs-lookup"><span data-stu-id="541f5-109">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="541f5-110">Çıkarsanabileceği en az kısıtlayıcı türü `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="541f5-110">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="541f5-111">, Örneğin, bir XML belgesi aşağıdaki parçası olur.</span><span class="sxs-lookup"><span data-stu-id="541f5-111">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 <span data-ttu-id="541f5-112">Yukarıdaki, ne zaman örnekte `attribute1` öznitelik değeri olan karşılaştı `6` tarafından <xref:System.Xml.Schema.XmlSchemaInference> işlemi varsayılır türünde olmasını `xs:unsignedByte`.</span><span class="sxs-lookup"><span data-stu-id="541f5-112">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="541f5-113">Zaman ikinci `parent` tarafından öğesiyle karşılaştı <xref:System.Xml.Schema.XmlSchemaInference> işlem, kısıtlaması izin vermek için gevşekleştirildiğini türüne değiştirerek `xs:string` çünkü değerini `attribute1` özniteliktir şimdi `A`.</span><span class="sxs-lookup"><span data-stu-id="541f5-113">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="541f5-114">Benzer şekilde, `minOccurs` özniteliği için tüm `child` şemada çıkarımı yapılan öğeleri izin vermek için gevşekleştirildiğini için `minOccurs="0"` ikinci ana öğesi alt öğe olduğundan.</span><span class="sxs-lookup"><span data-stu-id="541f5-114">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="541f5-115">XML belgelerden şemaları çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="541f5-115">Inferring Schemas from XML Documents</span></span>  
 <span data-ttu-id="541f5-116"><xref:System.Xml.Schema.XmlSchemaInference> Sınıfını kullanan iki aşırı <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> bir XML belgesi şemadan anlamak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="541f5-116">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="541f5-117">İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, bir XML belgesi dayalı bir şema oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="541f5-117">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="541f5-118">İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, birden çok XML belgelerini tanımlayan bir şema anlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="541f5-118">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="541f5-119">Örneğin, birden çok XML belgelerini besleyebilecek <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> XML belgeleri kümesinin tamamını tanımlayan bir şema oluşturmak için bir zaman yöntemi.</span><span class="sxs-lookup"><span data-stu-id="541f5-119">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="541f5-120">İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi oluşturur içinde yer alan bir XML belgesi şemadan bir <xref:System.Xml.XmlReader> nesne ve döndürür bir <xref:System.Xml.Schema.XmlSchemaSet> oluşturulursa şema içeren bir nesne.</span><span class="sxs-lookup"><span data-stu-id="541f5-120">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="541f5-121">İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi aramaları bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesi aynı hedef ad alanına sahip bir şema için XML belgesi yer alan olarak <xref:System.Xml.XmlReader> nesnesi, varolan şema iyileştirir ve döndürür bir <xref:System.Xml.Schema.XmlSchemaSet> oluşturulursa içeren nesnesi Şema.</span><span class="sxs-lookup"><span data-stu-id="541f5-121">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="541f5-122">Gelişmiş şema değişikliklerinin XML belgesinde bulunan yeni yapısı dayanır.</span><span class="sxs-lookup"><span data-stu-id="541f5-122">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="541f5-123">Örneğin, bir XML belgesi geçirildiği varsayımlar bulunan veri türleri hakkında yapılan ve şema oluşturulan bu varsayımları temel alarak.</span><span class="sxs-lookup"><span data-stu-id="541f5-123">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="541f5-124">Ancak, verileri, farklı bir ikinci çıkarım pass özgün varsayımına karşılaşılırsa, şema geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="541f5-124">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="541f5-125">Aşağıdaki örnek iyileştirme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="541f5-125">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="541f5-126">Aşağıdaki dosya örneğini alır `item1.xml`, ilk giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="541f5-126">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="541f5-127">Örnek sonra geçen `item2.xml` dosya ikinci giriş olarak:</span><span class="sxs-lookup"><span data-stu-id="541f5-127">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="541f5-128">Zaman `productID` öznitelik değeri ilk XML belgesinde karşılaştı `123456789` varsayılır bir `xs:unsignedInt` türü.</span><span class="sxs-lookup"><span data-stu-id="541f5-128">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="541f5-129">Ancak, ikinci bir XML belgesi olduğunda okuma ve değerini `A53-246` bulunan `xs:unsignedInt` türü artık olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="541f5-129">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="541f5-130">Şema geliştirilir ve türünü `productID` değiştirilir `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="541f5-130">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="541f5-131">Ayrıca, `minOccurs` için öznitelik `supplierID` ayarlanır `0`, ikinci bir XML belgesi Hayır içerdiğinden `supplierID` öğesi.</span><span class="sxs-lookup"><span data-stu-id="541f5-131">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="541f5-132">İlk XML belgesinden çıkarımı yapılan şema verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="541f5-132">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="541f5-133">İkinci bir XML belgesi iyileştirilmiştir ilk XML belgesindeki çıkarımı yapılan şema verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="541f5-133">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="541f5-134">Satır içi şemalar</span><span class="sxs-lookup"><span data-stu-id="541f5-134">Inline Schemas</span></span>  
 <span data-ttu-id="541f5-135">Satır içi bir XML Şeması Tanım Dili (XSD) şema sırasında karşılaşılan varsa <xref:System.Xml.Schema.XmlSchemaInference> işlemi, bir <xref:System.Xml.Schema.XmlSchemaInferenceException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="541f5-135">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="541f5-136">Örneğin, aşağıdaki satır içi şema atar bir <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span><span class="sxs-lookup"><span data-stu-id="541f5-136">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="541f5-137">Olamaz şemaları Refined</span><span class="sxs-lookup"><span data-stu-id="541f5-137">Schemas that Cannot be Refined</span></span>  
 <span data-ttu-id="541f5-138">Vardır W3C XML şema yapıları XML Şeması Tanım Dili (XSD) şeması <xref:System.Xml.Schema.XmlSchemaInference> işlem iyileştirmek ve bir özel durum oluşturulmasına neden için bir türü verildiyse işleyemez.</span><span class="sxs-lookup"><span data-stu-id="541f5-138">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="541f5-139">Bir karmaşık gibi üst düzey oluşturucuya bir sıra dışında her şey türüdür.</span><span class="sxs-lookup"><span data-stu-id="541f5-139">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="541f5-140">Şema nesne modeli (SOM)'da, bu karşılık gelen bir <xref:System.Xml.Schema.XmlSchemaComplexType> , <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> özelliği bir örneği değil <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="541f5-140">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541f5-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="541f5-141">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [<span data-ttu-id="541f5-142">XML şema nesne modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="541f5-142">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [<span data-ttu-id="541f5-143">Bir XML Şeması çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="541f5-143">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [<span data-ttu-id="541f5-144">Şema düğüm türleri ve yapısı çıkarımını yapma için kurallar</span><span class="sxs-lookup"><span data-stu-id="541f5-144">Rules for Inferring Schema Node Types and Structure</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
 [<span data-ttu-id="541f5-145">Basit türler çıkarımını yapma için kurallar</span><span class="sxs-lookup"><span data-stu-id="541f5-145">Rules for Inferring Simple Types</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
