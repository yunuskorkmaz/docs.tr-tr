---
title: XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: 61957ff88ef57703aff1861238ee10b23c2f16ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291610"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="6cfb4-102">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="6cfb4-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="6cfb4-103">XPath 2,0 veri modelinin bir örneği olarak, <xref:System.Xml.XPath.XPathNavigator> sınıfı ortak dil çalışma zamanı (CLR) türleriyle eşleşen kesin tür belirtilmiş verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="6cfb4-104">XPath 2,0 veri modeline göre yalnızca öğeler ve öznitelikler kesin türü belirtilmiş veri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly typed data.</span></span> <span data-ttu-id="6cfb4-105">Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> veya nesnesi içindeki verilere, türü <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> kesin belirlenmiş verilerin yanı sıra bir veri türünden diğerine dönüştürmeye yönelik mekanizmalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="6cfb4-106">XPathNavigator tarafından sunulan tür bilgileri</span><span class="sxs-lookup"><span data-stu-id="6cfb4-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="6cfb4-107">XML 1,0 verileri, bir DTD, XML şeması tanım dili (XSD) şeması veya başka bir mekanizmasıyla işlenmediği sürece Teknik olarak tür olmadan yapılır.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="6cfb4-108">Bir XML öğesi veya özniteliği ile ilişkilendirilebilen tür bilgileri kategorileri vardır.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="6cfb4-109">Basit CLR türleri: XML şema dillerinin hiçbiri doğrudan ortak dil çalışma zamanı (CLR) türlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="6cfb4-110">En uygun CLR türü olarak basit öğe ve öznitelik içeriğini görüntüleyebilmek yararlı olduğundan, tüm basit içerikler, <xref:System.String> eklenen herhangi bir şema bilgileriyle şema bilgileri yokluğunda olarak yazılabilir ve bu içeriği daha uygun bir türe göre iyileştiriyor.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="6cfb4-111">Özelliğini kullanarak, basit öğe ve öznitelik içeriğinin en iyi eşleşen CLR türünü bulabilirsiniz <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="6cfb4-112">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6cfb4-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="6cfb4-113">Basit (CLR) türleri listeleri: basit içeriğe sahip bir öğe veya öznitelik, boşluk ile ayrılmış bir değerler listesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="6cfb4-114">Değerler bir XML şeması tarafından bir "liste türü" olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="6cfb4-115">XML şeması yokluğunda, bu gibi basit içerik tek bir metin düğümü olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="6cfb4-116">Bir XML şeması kullanılabilir olduğunda, bu basit içerik her biri bir CLR nesneleri koleksiyonuyla eşleşen basit bir türe sahip bir dizi Atomik değer olarak gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="6cfb4-117">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6cfb4-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="6cfb4-118">Yazılan değer: şema tarafından doğrulanan bir öznitelik veya basit bir türe sahip öğe türü belirtilmiş bir değer içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="6cfb4-119">Bu değer, sayısal, dize veya tarih türü gibi temel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="6cfb4-120">XSD içindeki yerleşik basit türler, bir düğümün değerine yalnızca gibi daha uygun bir tür olarak erişim sağlayan CLR türleriyle eşleştirilebilir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="6cfb4-121">Öznitelikleri veya öğe alt öğesi olan bir öğe karmaşık bir tür olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="6cfb4-122">Basit içeriğe sahip bir karmaşık türün türü belirlenmiş değeri (yalnızca alt öğe olarak metin düğümleri), içeriğinin basit türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="6cfb4-123">Karmaşık içerik (bir veya daha fazla alt öğesi) olan bir karmaşık türün tür değeri, bir olarak döndürülen tüm alt metin düğümlerinin birleştirilmesiyle ilgili dize değeridir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="6cfb4-124">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6cfb4-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="6cfb4-125">Şema diline özgü tür adı: çoğu durumda, bir dış şema uygulamanın yan etkisi olarak ayarlanan CLR türleri, bir düğümün değerine erişim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="6cfb4-126">Ancak, bir XML belgesine uygulanan belirli bir şema ile ilişkili türü incelemek isteyebileceğiniz durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="6cfb4-127">Örneğin, ekli bir şemaya göre "PurchaseOrder" türünde içeriğe sahip olacak şekilde belirlenen tüm öğeleri ayıklayarak bir XML belgesinde arama yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="6cfb4-128">Bu tür bilgiler yalnızca şema doğrulamasının sonucu olarak ayarlanabilir ve bu bilgilere <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> sınıfının ve özellikleri aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="6cfb4-129">Daha fazla bilgi için aşağıdaki şema doğrulama bilgi kümesi (PSVı) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="6cfb4-130">Şemaya özgü tür yansıtma: başka durumlarda, bir XML belgesine uygulanan şemaya özgü türün daha ayrıntılı ayrıntılarını elde etmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="6cfb4-131">Örneğin, bir XML dosyası okurken, `maxOccurs` bazı özel hesaplamalar gerçekleştirmek IÇIN XML belgesindeki her bir geçerli düğüm için özniteliğini ayıklamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="6cfb4-132">Bu bilgiler yalnızca şema doğrulaması aracılığıyla ayarlandığından, <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> sınıfının özelliği aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="6cfb4-133">Daha fazla bilgi için aşağıdaki şema doğrulama bilgi kümesi (PSVı) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="6cfb4-134">XPathNavigator türü erişimciler</span><span class="sxs-lookup"><span data-stu-id="6cfb4-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="6cfb4-135">Aşağıdaki tabloda, <xref:System.Xml.XPath.XPathNavigator> bir düğümle ilgili tür bilgilerine erişmek için kullanılabilecek sınıfının çeşitli özellikleri ve yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="6cfb4-136">Özellik</span><span class="sxs-lookup"><span data-stu-id="6cfb4-136">Property</span></span>|<span data-ttu-id="6cfb4-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cfb4-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="6cfb4-138">Bu, geçerli olduğunda düğüm için XML Şeması tür bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="6cfb4-139">Bu, doğrulamadan sonra eklenen düğümün şema doğrulama doğrulaması bilgi kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="6cfb4-140">Bu, XML şema türü bilgilerinin yanı sıra geçerlilik bilgilerini de içerir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="6cfb4-141">Düğümün türü belirlenmiş değeri CLR türü.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="6cfb4-142">Düğümün içeriği, bir veya daha fazla CLR değeri olarak türü, düğümün XML şema türüyle en yakın eşleşme olan.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="6cfb4-143"><xref:System.String>Geçerli düğümün değeri <xref:System.Boolean> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:boolean` .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="6cfb4-144"><xref:System.String>Geçerli düğümün değeri <xref:System.DateTime> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:datetime` .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="6cfb4-145"><xref:System.String>Geçerli düğümün değeri <xref:System.Double> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xsd:double` .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="6cfb4-146"><xref:System.String>Geçerli düğümün değeri <xref:System.Int32> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:integer` .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="6cfb4-147"><xref:System.String>Geçerli düğümün değeri <xref:System.Int64> , için XPath 2,0 atama kurallarına göre bir değere dönüştürüldü `xs:integer` .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="6cfb4-148">Düğüm içeriği, XPath 2,0 atama kurallarına göre hedef türüne atama yapılır.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="6cfb4-149">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6cfb4-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="6cfb4-150">Şema sonrası doğrulama bilgi kümesi (PSVı)</span><span class="sxs-lookup"><span data-stu-id="6cfb4-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="6cfb4-151">Bir XML şeması işlemcisi, girdi olarak bir XML Infoset 'i kabul eder ve şema doğrulama bilgisi kümesine (PSVı) dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="6cfb4-152">PSVı, yeni bilgi öğeleri eklenen ve mevcut bilgi öğelerine eklenen yeni özellikler içeren özgün giriş XML bilgi kümesidir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="6cfb4-153">Tarafından sunulan PSVı içindeki XML Infoset 'e eklenen üç geniş bilgi sınıfı vardır <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="6cfb4-154">Doğrulama sonuçları: bir öğe veya özniteliğin başarıyla doğrulanıp doğrulanmayacağı hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="6cfb4-155">Bu, <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> sınıfının özelliğinin özelliği tarafından gösterilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="6cfb4-156">Varsayılan bilgiler: öğe veya öznitelik değerinin şemada belirtilen varsayılan değerlerle elde edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="6cfb4-157">Bu, <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> sınıfının özelliğinin özelliği tarafından gösterilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="6cfb4-158">Tür açıklamaları: tür tanımları veya öğe ve öznitelik bildirimleri olabilecek şema bileşenlerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="6cfb4-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A>Öğesinin özelliği, <xref:System.Xml.XPath.XPathNavigator> geçerli ise düğümün belirli tür bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="6cfb4-160">Bir düğümün geçerliliği bilinmiyorsa (örneğin, doğrulanıp daha sonra düzenlendiğinde).</span><span class="sxs-lookup"><span data-stu-id="6cfb4-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="6cfb4-161">sonra <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özellik olarak ayarlanır, `null` ancak sınıf özelliğinin farklı özelliklerinden tür bilgisi hala kullanılabilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="6cfb4-162">Aşağıdaki örnek, tarafından kullanıma sunulan gönderi şeması doğrulama bilgi kümesindeki bilgilerin kullanımını gösterir <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
 <span data-ttu-id="6cfb4-163">Örnek, `books.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="6cfb4-164">Örnek ayrıca `books.xsd` Şemayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="6cfb4-165">ValueAs özelliklerini kullanarak yazılan değerleri Al</span><span class="sxs-lookup"><span data-stu-id="6cfb4-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="6cfb4-166">Bir düğümün yazılan değeri <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> öğesinin özelliğine erişerek alınabilir <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="6cfb4-167">Belirli durumlarda, bir düğümün türü belirlenmiş değerini farklı bir türe dönüştürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="6cfb4-168">Ortak bir örnek, bir XML düğümünden sayısal bir değer almaya yönelik bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="6cfb4-169">Örneğin, aşağıdaki doğrulanmamış ve türsüz XML belgesini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="6cfb4-170">Öğesi üzerinde konumlandırılmışsa, özelliği olur, özelliği olur <xref:System.Xml.XPath.XPathNavigator> `price` <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> `null` <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> <xref:System.String> ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özellik dize olur `10.00` .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="6cfb4-171">Ancak,,,, <xref:System.Xml.XPath.XPathItem.ValueAs%2A> <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A> <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> veya <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> yöntemini ve özelliklerini kullanarak değeri sayısal bir değer olarak ayıklamak yine de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="6cfb4-172">Aşağıdaki örnek, yöntemini kullanarak böyle bir tür dönüştürme işlemini gösterir <xref:System.Xml.XPath.XPathItem.ValueAs%2A> .</span><span class="sxs-lookup"><span data-stu-id="6cfb4-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="6cfb4-173">Şema yerleşik türlerinden CLR türlerine eşleme hakkında daha fazla bilgi için bkz. [System. xml sınıflarında tür desteği](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6cfb4-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfb4-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cfb4-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="6cfb4-175">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="6cfb4-175">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="6cfb4-176">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="6cfb4-176">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="6cfb4-177">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="6cfb4-177">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="6cfb4-178">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="6cfb4-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="6cfb4-179">XPathNavigator Kullanarak XML Verilerini Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6cfb4-179">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)
