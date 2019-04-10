---
title: XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1905e9f1d80931bd15cff5f3d0a92ceee29435ef
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319891"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="85ccc-102">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="85ccc-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="85ccc-103">XPath 2.0 veri modeli, bir örneği olarak <xref:System.Xml.XPath.XPathNavigator> sınıfı, ortak dil çalışma zamanı (CLR) türleri ile eşleştirir, kesin türü belirtilmiş veri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="85ccc-104">XPath 2.0 veri modeline göre yalnızca öğeler ve öznitelikler kesin türü belirtilmiş veri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="85ccc-105"><xref:System.Xml.XPath.XPathNavigator> Sınıf içindeki verilerine erişmek için bir mekanizma sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> başka bir veri türünden dönüştürme mekanizmaları yanı sıra, kesin türü belirtilmiş veri nesnesi.</span><span class="sxs-lookup"><span data-stu-id="85ccc-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="85ccc-106">XPathNavigator tarafından kullanıma sunulan tür bilgileri</span><span class="sxs-lookup"><span data-stu-id="85ccc-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="85ccc-107">XML 1.0 verilerdir teknik türü sürece işlenen bir DTD'nin XML Şeması Tanım Dili (XSD) şemaya veya başka bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="85ccc-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="85ccc-108">Bir XML öğesi veya özniteliği ile ilişkilendirilebilen türü bilgi kategorilerde vardır.</span><span class="sxs-lookup"><span data-stu-id="85ccc-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
-   <span data-ttu-id="85ccc-109">Basit CLR türleri: XML şema diller hiçbiri doğrudan ortak dil çalışma zamanı (CLR) türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="85ccc-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="85ccc-110">Olarak basit bir öğe ve öznitelik içeriği en uygun CLR türü olarak görüntülemek yararlı olur çünkü tüm basit içerik yazılabilir <xref:System.String> tüm şema bilgileri olmadığında bu içerik için büyük olasılıkla iyileştirme şema bilgileri eklendi daha uygun bir tür.</span><span class="sxs-lookup"><span data-stu-id="85ccc-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="85ccc-111">CLR basit öğe ve öznitelik içerik türünü kullanarak eşleştirme en iyi bulabilirsiniz <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="85ccc-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="85ccc-112">Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="85ccc-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="85ccc-113">Basit (CLR) türleri listeler: Bir öğe veya öznitelik basit içeriğe sahip boşluk tarafından ayrılmış değerlerin bir listesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="85ccc-114">Bir "listesi türü." bir XML şeması tarafından belirtilen değerler</span><span class="sxs-lookup"><span data-stu-id="85ccc-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="85ccc-115">Bir XML Şeması olmaması durumunda tür basit içerik tek bir metin düğümü olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="85ccc-116">Bir XML Şeması kullanılabilir olduğunda, bir dizi atomik her CLR nesnelerin bir koleksiyona eşler basit bir tür olan değerleri gibi bu basit içerik sunulabilir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="85ccc-117">Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="85ccc-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="85ccc-118">Belirtilen değer: Bir şema doğrulanmış öznitelik veya öğenin basit bir tür ile yazılan bir değeri var.</span><span class="sxs-lookup"><span data-stu-id="85ccc-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="85ccc-119">Bu değer bir sayı, dize veya tarih türü gibi basit bir türdür.</span><span class="sxs-lookup"><span data-stu-id="85ccc-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="85ccc-120">CLR türleri, daha uygun bir tür yerine yalnızca bir düğümün değerini erişim sağlamak için tüm yerleşik basit türler XSD eşleştirilmiş olarak bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="85ccc-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="85ccc-121">Öznitelikleri veya alt öğesi olan bir öğe, bir karmaşık tür olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="85ccc-122">Basit içerik (yalnızca alt öğeleri olarak metin düğümleri) sahip bir karmaşık türü belirlenmiş değerini, kendi içerik basit türü aynıdır.</span><span class="sxs-lookup"><span data-stu-id="85ccc-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="85ccc-123">Karmaşık içerik (bir veya daha fazla alt öğe) sahip bir karmaşık türü belirlenmiş değerini birleştirme, tüm alt metin düğümleri olarak döndürülen dize değeridir bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="85ccc-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="85ccc-124">Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="85ccc-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="85ccc-125">Dil şeması belirli tür adı: Çoğu durumda, bir yan dış şeması uygulama etkisi olarak ayarlanır, CLR türleri, bir düğümün değerini erişim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85ccc-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="85ccc-126">Bununla birlikte, burada bir XML belgeye uygulanan belirli bir şema ile ilişkili tür incelemek isteyebilirsiniz durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="85ccc-127">Örneğin, bir XML belgesi arama "PurchaseOrder" eklenmiş bir şemaya göre içerik türü için belirlenen tüm öğeleri ayıklama isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85ccc-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="85ccc-128">Bu tür bilgileri yalnızca şema doğrulama sonucu olarak ayarlanabilir ve bu bilgileri aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> ve <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="85ccc-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="85ccc-129">Daha fazla bilgi için aşağıdaki sonrası Schema doğrulama bilgi kümesi (PSVI) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="85ccc-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
-   <span data-ttu-id="85ccc-130">Dil şeması belirli tür yansıma: Diğer durumlarda, daha fazla bir XML belgeye uygulanan şema özgü türü ayrıntılarını almak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85ccc-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="85ccc-131">Örneğin, bir XML dosyası okunurken ayıklamak istediğiniz `maxOccurs` öznitelik XML belgesindeki özel bir hesaplama gerçekleştirmek için geçerli her düğüm için.</span><span class="sxs-lookup"><span data-stu-id="85ccc-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="85ccc-132">Bu bilgiler yalnızca şema doğrulaması ayarlandığından aracılığıyla erişilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="85ccc-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="85ccc-133">Daha fazla bilgi için aşağıdaki sonrası Schema doğrulama bilgi kümesi (PSVI) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="85ccc-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="85ccc-134">XPathNavigator türü belirtilmiş erişimcileri</span><span class="sxs-lookup"><span data-stu-id="85ccc-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="85ccc-135">Aşağıdaki tabloda, çeşitli özellikleri ve yöntemleri gösterilmektedir <xref:System.Xml.XPath.XPathNavigator> bir düğüm türü bilgilerini erişmek için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="85ccc-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="85ccc-136">Özellik</span><span class="sxs-lookup"><span data-stu-id="85ccc-136">Property</span></span>|<span data-ttu-id="85ccc-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85ccc-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="85ccc-138">Geçerli ise bu düğüm için XML şema türü bilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="85ccc-139">Bu doğrulamadan sonra eklenen düğümünün Post şema doğrulama bilgi kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="85ccc-140">Bu, geçerlilik bilgi yanı sıra XML şema türü bilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="85ccc-141">Türü belirtilmiş bir düğümün değerini CLR türü.</span><span class="sxs-lookup"><span data-stu-id="85ccc-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="85ccc-142">Bir veya birden çok CLR türü değerleri gibi düğümünün düğüm XML şema türü için en yakın eşleşme içeriktir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="85ccc-143"><xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Boolean> XPath 2.0 atama kurallarına göre bir değer `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="85ccc-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="85ccc-144"><xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.DateTime> XPath 2.0 atama kurallarına göre bir değer `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="85ccc-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="85ccc-145"><xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Double> XPath 2.0 atama kurallarına göre bir değer `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="85ccc-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="85ccc-146"><xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Int32> XPath 2.0 atama kurallarına göre bir değer `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="85ccc-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="85ccc-147"><xref:System.String> Değeri geçerli düğümün değerine bir <xref:System.Int64> XPath 2.0 atama kurallarına göre bir değer `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="85ccc-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="85ccc-148">XPath 2.0 atama kurallara göre hedef türüne cast düğüm içeriği.</span><span class="sxs-lookup"><span data-stu-id="85ccc-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="85ccc-149">Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="85ccc-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="85ccc-150">Sonrası Schema doğrulama bilgi kümesi (PSVI)</span><span class="sxs-lookup"><span data-stu-id="85ccc-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="85ccc-151">Bir XML Şeması işlemci bir XML bilgi kümesi girdi olarak kabul eder ve bir sonrası Schema doğrulama bilgi kümesi (PSVI) içine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="85ccc-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="85ccc-152">Bir PSVI yeni eklenen bilgi öğeleri ve bilgi öğelere eklenen yeni özellikleri özgün giriş XML bilgi kümesi olur.</span><span class="sxs-lookup"><span data-stu-id="85ccc-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="85ccc-153">XML bilgi kümesi tarafından kullanıma sunulan PSVI içinde eklenen bilgilerin geniş üç sınıfı vardır <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="85ccc-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="85ccc-154">Doğrulama sonuçları: Olup bir öğe veya öznitelik başarıyla veya doğrulandı dair bilgiler.</span><span class="sxs-lookup"><span data-stu-id="85ccc-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="85ccc-155">Tarafından sunulan bu <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="85ccc-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="85ccc-156">Varsayılan bilgileri: Göstergelerden eklenebilir olup varsayılan değerleri veya şemasında belirtilen öğe veya öznitelik değeri alındı.</span><span class="sxs-lookup"><span data-stu-id="85ccc-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="85ccc-157">Tarafından sunulan bu <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="85ccc-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="85ccc-158">Tür ek açıklamaları: Tür tanımları veya öğe ve öznitelik bildirimleri şema bileşenleri başvurular.</span><span class="sxs-lookup"><span data-stu-id="85ccc-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="85ccc-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> geçerli olup olmadığını düğümünün belirli tür bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="85ccc-160">Geçerlilik düğümünün, ne zaman, ardından daha sonra doğrulandı gibi bilinmiyorsa düzenlendi.</span><span class="sxs-lookup"><span data-stu-id="85ccc-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="85ccc-161">ardından <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği `null` ancak tür bilgileri çeşitli özelliklerini hala kullanılabilir <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="85ccc-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="85ccc-162">Sonrası Schema doğrulama bilgi tarafından kullanıma sunulan kümesi içindeki bilgileri kullanarak aşağıdaki örnekte gösterilmiştir <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="85ccc-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
 <span data-ttu-id="85ccc-163">Örnek alan `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="85ccc-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="85ccc-164">Bu örnek ayrıca alır `books.xsd` giriş olarak şema.</span><span class="sxs-lookup"><span data-stu-id="85ccc-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="85ccc-165">Değerlerini özellikleri kullanılarak yazılan değerler elde</span><span class="sxs-lookup"><span data-stu-id="85ccc-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="85ccc-166">Türü belirtilmiş bir düğümün değerini erişerek alınabilir <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliği <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="85ccc-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="85ccc-167">Bazı durumlarda, belirlenmiş bir düğümün değerini farklı bir türe dönüştürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85ccc-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="85ccc-168">Bir XML düğümünü sayısal değer alma yaygın bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="85ccc-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="85ccc-169">Örneğin, aşağıdaki doğrulanmamış ve türü belirsiz XML belgesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="85ccc-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="85ccc-170">Varsa <xref:System.Xml.XPath.XPathNavigator> üzerinde konumlandırılmış `price` öğesi <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> özelliği olacaktır `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> özellik olacak <xref:System.String>ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özelliği, bir dize olacak `10.00`.</span><span class="sxs-lookup"><span data-stu-id="85ccc-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="85ccc-171">Ancak, yine de kullanarak bir sayısal değer olarak değerini ayıklamak mümkün <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, veya <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> yöntem ve özellikleri.</span><span class="sxs-lookup"><span data-stu-id="85ccc-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="85ccc-172">Aşağıdaki örnekte, böyle bir dönüştürme gerçekleştirme gösterilmektedir <xref:System.Xml.XPath.XPathItem.ValueAs%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="85ccc-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="85ccc-173">Eşleme Şeması yerleşik türler CLR türleri hakkında daha fazla bilgi için bkz. [System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="85ccc-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ccc-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85ccc-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="85ccc-175">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="85ccc-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="85ccc-176">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="85ccc-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="85ccc-177">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="85ccc-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="85ccc-178">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="85ccc-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="85ccc-179">XPathNavigator Kullanarak XML Verilerini Ayıklama</span><span class="sxs-lookup"><span data-stu-id="85ccc-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
