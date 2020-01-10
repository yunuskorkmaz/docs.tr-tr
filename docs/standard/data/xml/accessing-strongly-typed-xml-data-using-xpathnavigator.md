---
title: XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: ec08b668bf54c5460e078bbb27bfbc370aff4e4a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711187"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="0dbe2-102">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="0dbe2-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="0dbe2-103">XPath 2,0 veri modelinin bir örneği olarak <xref:System.Xml.XPath.XPathNavigator> sınıfı, ortak dil çalışma zamanı (CLR) türleriyle eşleşen kesin türü belirtilmiş verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="0dbe2-104">XPath 2,0 veri modeline göre yalnızca öğeler ve öznitelikler kesin türü belirtilmiş veri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="0dbe2-105"><xref:System.Xml.XPath.XPathNavigator> sınıfı, bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi içindeki verilere, türü kesin belirlenmiş verilerin yanı sıra bir veri türünden diğerine dönüştürmeye yönelik mekanizmalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="0dbe2-106">XPathNavigator tarafından sunulan tür bilgileri</span><span class="sxs-lookup"><span data-stu-id="0dbe2-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="0dbe2-107">XML 1,0 verileri, bir DTD, XML şeması tanım dili (XSD) şeması veya başka bir mekanizmasıyla işlenmediği sürece Teknik olarak tür olmadan yapılır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="0dbe2-108">Bir XML öğesi veya özniteliği ile ilişkilendirilebilen tür bilgileri kategorileri vardır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="0dbe2-109">Basit CLR türleri: XML şema dillerinin hiçbiri doğrudan ortak dil çalışma zamanı (CLR) türlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="0dbe2-110">En uygun CLR türü olarak basit öğe ve öznitelik içeriğini görüntüleyebilmek yararlı olduğundan, tüm basit içerikler, eklenen tüm şema bilgileriyle şema bilgileri yokluğunda <xref:System.String> olarak yazılabilir ve bu içeriği daha uygun bir türe göre iyileştiriyor.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="0dbe2-111"><xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özelliğini kullanarak, basit öğe ve öznitelik içeriğinin en iyi eşleşen CLR türünü bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="0dbe2-112">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe2-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="0dbe2-113">Basit (CLR) türleri listeleri: basit içeriğe sahip bir öğe veya öznitelik, boşluk ile ayrılmış bir değerler listesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="0dbe2-114">Değerler bir XML şeması tarafından bir "liste türü" olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="0dbe2-115">XML şeması yokluğunda, bu gibi basit içerik tek bir metin düğümü olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="0dbe2-116">Bir XML şeması kullanılabilir olduğunda, bu basit içerik her biri bir CLR nesneleri koleksiyonuyla eşleşen basit bir türe sahip bir dizi Atomik değer olarak gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="0dbe2-117">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe2-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="0dbe2-118">Yazılan değer: şema tarafından doğrulanan bir öznitelik veya basit bir türe sahip öğe türü belirtilmiş bir değer içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="0dbe2-119">Bu değer, sayısal, dize veya tarih türü gibi temel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="0dbe2-120">XSD içindeki yerleşik basit türler, bir düğümün değerine yalnızca <xref:System.String>olarak değil, daha uygun bir tür olarak erişim sağlayan CLR türleriyle eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="0dbe2-121">Öznitelikleri veya öğe alt öğesi olan bir öğe karmaşık bir tür olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="0dbe2-122">Basit içeriğe sahip bir karmaşık türün türü belirlenmiş değeri (yalnızca alt öğe olarak metin düğümleri), içeriğinin basit türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="0dbe2-123">Karmaşık içerik (bir veya daha fazla alt öğesi) olan bir karmaşık türün tür değeri, bir <xref:System.String>olarak döndürülen tüm alt metin düğümlerinin birleştirilmesiyle ilgili dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="0dbe2-124">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe2-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="0dbe2-125">Şema diline özgü tür adı: çoğu durumda, bir dış şema uygulamanın yan etkisi olarak ayarlanan CLR türleri, bir düğümün değerine erişim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="0dbe2-126">Ancak, bir XML belgesine uygulanan belirli bir şema ile ilişkili türü incelemek isteyebileceğiniz durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="0dbe2-127">Örneğin, ekli bir şemaya göre "PurchaseOrder" türünde içeriğe sahip olacak şekilde belirlenen tüm öğeleri ayıklayarak bir XML belgesinde arama yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="0dbe2-128">Bu tür bilgiler, yalnızca şema doğrulamasının sonucu olarak ayarlanabilir ve bu bilgilere <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> ve <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özellikleri aracılığıyla erişilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="0dbe2-129">Daha fazla bilgi için aşağıdaki şema doğrulama bilgi kümesi (PSVı) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="0dbe2-130">Şemaya özgü tür yansıtma: başka durumlarda, bir XML belgesine uygulanan şemaya özgü türün daha ayrıntılı ayrıntılarını elde etmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="0dbe2-131">Örneğin, bir XML dosyası okurken, bazı özel hesaplamalar gerçekleştirmek için XML belgesindeki her bir geçerli düğüm için `maxOccurs` özniteliğini ayıklamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="0dbe2-132">Bu bilgiler yalnızca şema doğrulaması aracılığıyla ayarlandığından, <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği aracılığıyla erişilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="0dbe2-133">Daha fazla bilgi için aşağıdaki şema doğrulama bilgi kümesi (PSVı) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="0dbe2-134">XPathNavigator türü erişimciler</span><span class="sxs-lookup"><span data-stu-id="0dbe2-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="0dbe2-135">Aşağıdaki tabloda, bir düğümle ilgili tür bilgilerine erişmek için kullanılabilecek <xref:System.Xml.XPath.XPathNavigator> sınıfının çeşitli özellikleri ve yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="0dbe2-136">Özellik</span><span class="sxs-lookup"><span data-stu-id="0dbe2-136">Property</span></span>|<span data-ttu-id="0dbe2-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dbe2-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="0dbe2-138">Bu, geçerli olduğunda düğüm için XML Şeması tür bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="0dbe2-139">Bu, doğrulamadan sonra eklenen düğümün şema doğrulama doğrulaması bilgi kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="0dbe2-140">Bu, XML şema türü bilgilerinin yanı sıra geçerlilik bilgilerini de içerir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="0dbe2-141">Düğümün türü belirlenmiş değeri CLR türü.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="0dbe2-142">Düğümün içeriği, bir veya daha fazla CLR değeri olarak türü, düğümün XML şema türüyle en yakın eşleşme olan.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="0dbe2-143">Geçerli düğümün <xref:System.String> değeri, `xs:boolean`için XPath 2,0 atama kurallarına göre <xref:System.Boolean> bir değere dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="0dbe2-144">Geçerli düğümün <xref:System.String> değeri, `xs:datetime`için XPath 2,0 atama kurallarına göre <xref:System.DateTime> bir değere dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="0dbe2-145">Geçerli düğümün <xref:System.String> değeri, `xsd:double`için XPath 2,0 atama kurallarına göre <xref:System.Double> bir değere dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="0dbe2-146">Geçerli düğümün <xref:System.String> değeri, `xs:integer`için XPath 2,0 atama kurallarına göre <xref:System.Int32> bir değere dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="0dbe2-147">Geçerli düğümün <xref:System.String> değeri, `xs:integer`için XPath 2,0 atama kurallarına göre <xref:System.Int64> bir değere dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="0dbe2-148">Düğüm içeriği, XPath 2,0 atama kurallarına göre hedef türüne atama yapılır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="0dbe2-149">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe2-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="0dbe2-150">Şema sonrası doğrulama bilgi kümesi (PSVı)</span><span class="sxs-lookup"><span data-stu-id="0dbe2-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="0dbe2-151">Bir XML şeması işlemcisi, girdi olarak bir XML Infoset 'i kabul eder ve şema doğrulama bilgisi kümesine (PSVı) dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="0dbe2-152">PSVı, yeni bilgi öğeleri eklenen ve mevcut bilgi öğelerine eklenen yeni özellikler içeren özgün giriş XML bilgi kümesidir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="0dbe2-153"><xref:System.Xml.XPath.XPathNavigator>tarafından kullanıma sunulan PSVı içindeki XML Infoset 'e eklenen üç geniş bilgi sınıfı vardır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="0dbe2-154">Doğrulama sonuçları: bir öğe veya özniteliğin başarıyla doğrulanıp doğrulanmayacağı hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="0dbe2-155">Bu, <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliğinin <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> özelliği tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="0dbe2-156">Varsayılan bilgiler: öğe veya öznitelik değerinin şemada belirtilen varsayılan değerlerle elde edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="0dbe2-157">Bu, <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliğinin <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> özelliği tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="0dbe2-158">Tür açıklamaları: tür tanımları veya öğe ve öznitelik bildirimleri olabilecek şema bileşenlerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="0dbe2-159"><xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği, geçerli olduğunda düğümün belirli tür bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="0dbe2-160">Bir düğümün geçerliliği bilinmiyorsa (örneğin, doğrulanıp daha sonra düzenlendiğinde).</span><span class="sxs-lookup"><span data-stu-id="0dbe2-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="0dbe2-161"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Özellik `null` olarak ayarlanır, ancak <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliğinin çeşitli özelliklerinden tür bilgileri hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="0dbe2-162">Aşağıdaki örnek, <xref:System.Xml.XPath.XPathNavigator>tarafından kullanıma sunulan gönderi şeması doğrulama bilgi kümesindeki bilgilerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="0dbe2-163">Örnek, `books.xml` dosyasını girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="0dbe2-164">Örnek ayrıca `books.xsd` şemasını giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"   
attributeFormDefault="unqualified" elementFormDefault="qualified"   
targetNamespace="http://www.contoso.com/books"   
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="0dbe2-165">ValueAs özelliklerini kullanarak yazılan değerleri Al</span><span class="sxs-lookup"><span data-stu-id="0dbe2-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="0dbe2-166">Bir düğümün yazılan değeri, <xref:System.Xml.XPath.XPathNavigator><xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliğine erişerek alınabilir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="0dbe2-167">Belirli durumlarda, bir düğümün türü belirlenmiş değerini farklı bir türe dönüştürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="0dbe2-168">Ortak bir örnek, bir XML düğümünden sayısal bir değer almaya yönelik bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="0dbe2-169">Örneğin, aşağıdaki doğrulanmamış ve türsüz XML belgesini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="0dbe2-170"><xref:System.Xml.XPath.XPathNavigator> `price` öğesinde konumlandırılmışsa <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği `null`olur, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özelliği <xref:System.String>ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliği dize `10.00`olur.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="0dbe2-171">Ancak, <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>veya <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> Yöntem ve özellikleri kullanılarak değeri sayısal bir değer olarak ayıklamak yine de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="0dbe2-172">Aşağıdaki örnek, <xref:System.Xml.XPath.XPathItem.ValueAs%2A> yöntemi kullanılarak bu tür bir dönüştürmeyi gerçekleştirmenizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="0dbe2-173">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe2-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dbe2-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dbe2-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="0dbe2-175">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="0dbe2-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="0dbe2-176">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="0dbe2-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="0dbe2-177">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="0dbe2-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="0dbe2-178">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="0dbe2-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="0dbe2-179">XPathNavigator Kullanarak XML Verilerini Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0dbe2-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
