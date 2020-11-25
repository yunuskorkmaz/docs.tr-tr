---
title: Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları
ms.date: 03/30/2017
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
ms.openlocfilehash: e49e50dc21951d739b12cdfa60c6a48f67576873
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697603"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a><span data-ttu-id="73db9-102">Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları</span><span class="sxs-lookup"><span data-stu-id="73db9-102">Rules for Inferring Schema Node Types and Structure</span></span>

<span data-ttu-id="73db9-103">Bu konuda, şema çıkarımı işleminin bir XML belgesindeki düğüm türlerini bir XML şeması tanım dili (XSD) yapısına nasıl dönüştürdüğünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73db9-103">This topic describes how the schema inference process translates the node types in an XML document to an XML Schema definition language (XSD) structure.</span></span>  
  
## <a name="element-inference-rules"></a><span data-ttu-id="73db9-104">Öğe çıkarım kuralları</span><span class="sxs-lookup"><span data-stu-id="73db9-104">Element Inference Rules</span></span>  

 <span data-ttu-id="73db9-105">Bu bölümde, öğe bildirimleri için çıkarım kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73db9-105">This section describes the inference rules for element declarations.</span></span> <span data-ttu-id="73db9-106">Çıkarsanmayacak öğe bildirimlerinin sekiz yapısı vardır:</span><span class="sxs-lookup"><span data-stu-id="73db9-106">There are eight structures of element declarations that will be inferred:</span></span>  
  
1. <span data-ttu-id="73db9-107">Basit türdeki öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-107">Element of simple type</span></span>  
  
2. <span data-ttu-id="73db9-108">Boş öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-108">Empty element</span></span>  
  
3. <span data-ttu-id="73db9-109">Öznitelikleri olan boş öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-109">Empty element with attributes</span></span>  
  
4. <span data-ttu-id="73db9-110">Öznitelikleri ve basit içeriği olan öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-110">Element with attributes and simple content</span></span>  
  
5. <span data-ttu-id="73db9-111">Alt öğeleri dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-111">Element with a sequence of child elements</span></span>  
  
6. <span data-ttu-id="73db9-112">Alt öğeler ve öznitelikler dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-112">Element with a sequence of child elements and attributes</span></span>  
  
7. <span data-ttu-id="73db9-113">Alt öğelerin seçim dizisine sahip öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-113">Element with a sequence of choices of child elements</span></span>  
  
8. <span data-ttu-id="73db9-114">Alt öğe ve özniteliklerin bir dizi seçimi olan öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-114">Element with a sequence of choices of child elements and attributes</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73db9-115">Tüm `complexType` Bildirimler anonim türler olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="73db9-115">All `complexType` declarations are inferred as anonymous types.</span></span> <span data-ttu-id="73db9-116">Çıkarılan tek genel öğe kök öğesidir; diğer tüm öğeler yereldir.</span><span class="sxs-lookup"><span data-stu-id="73db9-116">The only global element inferred is the root element; all other elements are local.</span></span>  
  
 <span data-ttu-id="73db9-117">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-117">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
### <a name="simple-typed-element"></a><span data-ttu-id="73db9-118">Basit tür belirtilmiş öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-118">Simple Typed Element</span></span>  

 <span data-ttu-id="73db9-119">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-119">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-120">Kalın öğe, basit tür öğesi için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-120">The bolded element shows the schema inferred for the simple type element.</span></span>  
  
 <span data-ttu-id="73db9-121">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-121">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-122">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-122">XML</span></span>|<span data-ttu-id="73db9-123">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-123">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a><span data-ttu-id="73db9-124">Boş öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-124">Empty Element</span></span>  

 <span data-ttu-id="73db9-125">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-125">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-126">Kalın öğe, boş öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-126">The bolded element shows the schema inferred for the empty element.</span></span>  
  
 <span data-ttu-id="73db9-127">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-127">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-128">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-128">XML</span></span>|<span data-ttu-id="73db9-129">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-129">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a><span data-ttu-id="73db9-130">Öznitelikleri olan boş öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-130">Empty Element with Attributes</span></span>  

 <span data-ttu-id="73db9-131">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-131">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-132">Kalın öğeler, özniteliklerin bulunduğu boş öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-132">The bolded elements show the schema inferred for the empty element with attributes.</span></span>  
  
 <span data-ttu-id="73db9-133">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-133">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-134">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-134">XML</span></span>|<span data-ttu-id="73db9-135">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-135">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a><span data-ttu-id="73db9-136">Öznitelikleri ve basit Içeriği olan öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-136">Element with Attributes and Simple Content</span></span>  

 <span data-ttu-id="73db9-137">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-137">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-138">Kalın öğeler, öznitelikleri ve basit içeriği olan bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-138">The bolded elements show the schema inferred for an element with attributes and simple content.</span></span>  
  
 <span data-ttu-id="73db9-139">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-139">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-140">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-140">XML</span></span>|<span data-ttu-id="73db9-141">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-141">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a><span data-ttu-id="73db9-142">Alt öğeleri dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-142">Element with a Sequence of Child Elements</span></span>  

 <span data-ttu-id="73db9-143">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-143">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-144">Kalın öğeler, alt öğeleri dizisi olan bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-144">The bolded elements show the schema inferred for an element with a sequence of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73db9-145">Bir öğenin yalnızca bir alt öğesi olsa bile, yine de bir sıra olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="73db9-145">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="73db9-146">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-146">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-147">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-147">XML</span></span>|<span data-ttu-id="73db9-148">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-148">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a><span data-ttu-id="73db9-149">Alt öğeler ve öznitelikler dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-149">Element with a Sequence of Child Elements and Attributes</span></span>  

 <span data-ttu-id="73db9-150">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-150">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-151">Kalın öğeler, alt öğe ve özniteliklerin sırası olan bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-151">The bolded elements show the schema inferred for an element with a sequence of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73db9-152">Bir öğenin yalnızca bir alt öğesi olsa bile, yine de bir sıra olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="73db9-152">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="73db9-153">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-153">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-154">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-154">XML</span></span>|<span data-ttu-id="73db9-155">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-155">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a><span data-ttu-id="73db9-156">Alt öğelerin sırası ve seçimlerine sahip öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-156">Element with a Sequence and Choices of Child Elements</span></span>  

 <span data-ttu-id="73db9-157">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-157">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-158">Kalın öğeler, bir öğe için gösterilen şemayı bir dizi ve tercih edilen alt öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-158">The bolded elements show the schema inferred for an element with a sequence and choice of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73db9-159">`maxOccurs`Öğesinin özniteliği, `xs:choice` `"unbounded"` gösterilen şemada olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="73db9-159">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="73db9-160">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-160">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-161">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-161">XML</span></span>|<span data-ttu-id="73db9-162">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-162">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a><span data-ttu-id="73db9-163">Alt öğe ve özniteliklerin sırası ve seçimi içeren öğe</span><span class="sxs-lookup"><span data-stu-id="73db9-163">Element with a Sequence and Choice of Child Elements and Attributes</span></span>  

 <span data-ttu-id="73db9-164">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db9-164">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="73db9-165">Kalın öğeler, alt öğe ve özniteliklerin sırası ve seçimi içeren bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="73db9-165">The bolded elements show the schema inferred for an element with a sequence and choice of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73db9-166">`maxOccurs`Öğesinin özniteliği, `xs:choice` `"unbounded"` gösterilen şemada olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="73db9-166">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="73db9-167">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-167">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="73db9-168">XML</span><span class="sxs-lookup"><span data-stu-id="73db9-168">XML</span></span>|<span data-ttu-id="73db9-169">Şema</span><span class="sxs-lookup"><span data-stu-id="73db9-169">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a><span data-ttu-id="73db9-170">Öznitelik Işleme</span><span class="sxs-lookup"><span data-stu-id="73db9-170">Attribute Processing</span></span>  

 <span data-ttu-id="73db9-171">Düğüm içinde yeni bir özniteliğe her karşılaşıldığında, bu, ile düğümün çıkarılan tanımına eklenir `use="required"` .</span><span class="sxs-lookup"><span data-stu-id="73db9-171">Whenever a new attribute is encountered within a node, it is added to the inferred definition of the node with `use="required"`.</span></span> <span data-ttu-id="73db9-172">Örnekte aynı düğüm bir sonraki sefer olduğunda, çıkarım işlemi geçerli örneğin özniteliklerini zaten çıkartılan olanlarla karşılaştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="73db9-172">The next time the same node is found in the instance, the inference process will compare attributes of the current instance with the ones already inferred.</span></span> <span data-ttu-id="73db9-173">Örnekte zaten başka bir görünenler varsa, `use="optional"` öznitelik tanımına eklenir.</span><span class="sxs-lookup"><span data-stu-id="73db9-173">If some of the already inferred ones are missing in the instance, `use="optional"` is added to the attribute definition.</span></span> <span data-ttu-id="73db9-174">Yeni öznitelikler ile var olan bildirimlere eklenir `use="optional"` .</span><span class="sxs-lookup"><span data-stu-id="73db9-174">New attributes are added to existing declarations with `use="optional"`.</span></span>  
  
### <a name="occurrence-constraints"></a><span data-ttu-id="73db9-175">Oluşum kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="73db9-175">Occurrence Constraints</span></span>  

 <span data-ttu-id="73db9-176">Şema çıkarımı işlemi sırasında, `minOccurs` ve `maxOccurs` öznitelikleri, bir şemanın Çıkarsanan bileşenleri için, `"0"` veya `"1"` ve ya da değerleri oluşturulur `"1"` `"unbounded"` .</span><span class="sxs-lookup"><span data-stu-id="73db9-176">During the schema inference process, the `minOccurs` and `maxOccurs` attributes are generated, for inferred components of a schema, with the values `"0"` or `"1"` and `"1"` or `"unbounded"`.</span></span> <span data-ttu-id="73db9-177">Değerler `"1"` ve `"unbounded"` yalnızca değerler `"0"` ve `"1"` XML belgesini doğrulayamıyorsa kullanılır (örneğin, `MinOccurs="0"` bir öğeyi doğru bir şekilde açıklamıyorsa, `minOccurs="1"` kullanılır).</span><span class="sxs-lookup"><span data-stu-id="73db9-177">The values `"1"` and `"unbounded"` are used only when the values `"0"` and `"1"` cannot validate the XML document (for example, if `MinOccurs="0"` does not accurately describe an element, `minOccurs="1"` is used).</span></span>  
  
### <a name="mixed-content"></a><span data-ttu-id="73db9-178">Karışık Içerik</span><span class="sxs-lookup"><span data-stu-id="73db9-178">Mixed Content</span></span>  

 <span data-ttu-id="73db9-179">Bir öğe, karışık içerik içeriyorsa (örneğin, öğelerle birlikte metin oluşturma), bu öznitelik, `mixed="true"` gösterilen karmaşık tür tanımı için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73db9-179">If an element contains mixed content (for example text interspersed with elements), the `mixed="true"` attribute is generated for the inferred complex type definition.</span></span>  
  
## <a name="other-node-type-inference-rules"></a><span data-ttu-id="73db9-180">Diğer düğüm türü çıkarımı kuralları</span><span class="sxs-lookup"><span data-stu-id="73db9-180">Other Node Type Inference Rules</span></span>  

 <span data-ttu-id="73db9-181">Aşağıdaki tabloda yönerge, açıklama, varlık başvurusu, CDATA, belge türü ve ad alanı düğümlerini işlemek için çıkarım kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73db9-181">The following table describes the inference rules for processing instruction, comment, entity reference, CDATA, document type, and namespace nodes.</span></span>  
  
|<span data-ttu-id="73db9-182">Düğüm türü</span><span class="sxs-lookup"><span data-stu-id="73db9-182">Node Type</span></span>|<span data-ttu-id="73db9-183">Çeviri</span><span class="sxs-lookup"><span data-stu-id="73db9-183">Translation</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73db9-184">İşlem yönergesi</span><span class="sxs-lookup"><span data-stu-id="73db9-184">Processing instruction</span></span>|<span data-ttu-id="73db9-185">LIP.</span><span class="sxs-lookup"><span data-stu-id="73db9-185">Ignored.</span></span>|  
|<span data-ttu-id="73db9-186">Yorum</span><span class="sxs-lookup"><span data-stu-id="73db9-186">Comment</span></span>|<span data-ttu-id="73db9-187">LIP.</span><span class="sxs-lookup"><span data-stu-id="73db9-187">Ignored.</span></span>|  
|<span data-ttu-id="73db9-188">Varlık başvurusu</span><span class="sxs-lookup"><span data-stu-id="73db9-188">Entity reference</span></span>|<span data-ttu-id="73db9-189"><xref:System.Xml.Schema.XmlSchemaInference>Sınıf, varlık başvurularını işlemez.</span><span class="sxs-lookup"><span data-stu-id="73db9-189">The <xref:System.Xml.Schema.XmlSchemaInference> class does not handle entity references.</span></span> <span data-ttu-id="73db9-190">Bir XML belgesi varlık başvuruları içeriyorsa, varlıkları genişleten bir okuyucu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73db9-190">If an XML document contains entity references, you need to use a reader that expands the entities.</span></span> <span data-ttu-id="73db9-191">Örneğin, <xref:System.Xml.XmlTextReader> <xref:System.Xml.XmlTextReader.EntityHandling%2A> özelliğini bir parametre olarak ayarlanmış şekilde bir ile geçirebilirsiniz <xref:System.Xml.EntityHandling.ExpandEntities> .</span><span class="sxs-lookup"><span data-stu-id="73db9-191">For example, you can pass an <xref:System.Xml.XmlTextReader> with the <xref:System.Xml.XmlTextReader.EntityHandling%2A> property set to <xref:System.Xml.EntityHandling.ExpandEntities> as a parameter.</span></span> <span data-ttu-id="73db9-192">Varlık başvurularına karşılaşılırsa ve okuyucu varlıkları genişletmezse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73db9-192">If entity references are encountered and the reader does not expand entities, an exception is throw.</span></span>|  
|<span data-ttu-id="73db9-193">CDATA</span><span class="sxs-lookup"><span data-stu-id="73db9-193">CDATA</span></span>|<span data-ttu-id="73db9-194">`<![CDATA[ … ]]`XML belgesindeki tüm bölümler, olarak algılanır `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="73db9-194">Any `<![CDATA[ … ]]` sections in an XML document will be inferred as `xs:string`.</span></span>|  
|<span data-ttu-id="73db9-195">Belge türü</span><span class="sxs-lookup"><span data-stu-id="73db9-195">Document type</span></span>|<span data-ttu-id="73db9-196">LIP.</span><span class="sxs-lookup"><span data-stu-id="73db9-196">Ignored.</span></span>|  
|<span data-ttu-id="73db9-197">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="73db9-197">Namespaces</span></span>|<span data-ttu-id="73db9-198">LIP.</span><span class="sxs-lookup"><span data-stu-id="73db9-198">Ignored.</span></span>|  
  
 <span data-ttu-id="73db9-199">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="73db9-199">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73db9-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73db9-200">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="73db9-201">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="73db9-201">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="73db9-202">XML Şemasından Çıkarım Yapma</span><span class="sxs-lookup"><span data-stu-id="73db9-202">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="73db9-203">XML Belgelerinden Şema Çıkarımı Yapma</span><span class="sxs-lookup"><span data-stu-id="73db9-203">Inferring Schemas from XML Documents</span></span>](inferring-schemas-from-xml-documents.md)
- [<span data-ttu-id="73db9-204">Basit Türlerin Çıkarımını Yapma Kuralları</span><span class="sxs-lookup"><span data-stu-id="73db9-204">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
