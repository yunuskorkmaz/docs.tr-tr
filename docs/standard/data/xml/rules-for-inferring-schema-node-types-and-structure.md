---
description: 'Hakkında daha fazla bilgi edinin: şema düğümü türlerini ve yapısını edinme kuralları'
title: Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları
ms.date: 03/30/2017
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
ms.openlocfilehash: cbcc60a4c2510fb75aa5194164881f573f1a688f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783033"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a><span data-ttu-id="25bdb-103">Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları</span><span class="sxs-lookup"><span data-stu-id="25bdb-103">Rules for Inferring Schema Node Types and Structure</span></span>

<span data-ttu-id="25bdb-104">Bu konuda, şema çıkarımı işleminin bir XML belgesindeki düğüm türlerini bir XML şeması tanım dili (XSD) yapısına nasıl dönüştürdüğünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25bdb-104">This topic describes how the schema inference process translates the node types in an XML document to an XML Schema definition language (XSD) structure.</span></span>  
  
## <a name="element-inference-rules"></a><span data-ttu-id="25bdb-105">Öğe çıkarım kuralları</span><span class="sxs-lookup"><span data-stu-id="25bdb-105">Element Inference Rules</span></span>  

 <span data-ttu-id="25bdb-106">Bu bölümde, öğe bildirimleri için çıkarım kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25bdb-106">This section describes the inference rules for element declarations.</span></span> <span data-ttu-id="25bdb-107">Çıkarsanmayacak öğe bildirimlerinin sekiz yapısı vardır:</span><span class="sxs-lookup"><span data-stu-id="25bdb-107">There are eight structures of element declarations that will be inferred:</span></span>  
  
1. <span data-ttu-id="25bdb-108">Basit türdeki öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-108">Element of simple type</span></span>  
  
2. <span data-ttu-id="25bdb-109">Boş öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-109">Empty element</span></span>  
  
3. <span data-ttu-id="25bdb-110">Öznitelikleri olan boş öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-110">Empty element with attributes</span></span>  
  
4. <span data-ttu-id="25bdb-111">Öznitelikleri ve basit içeriği olan öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-111">Element with attributes and simple content</span></span>  
  
5. <span data-ttu-id="25bdb-112">Alt öğeleri dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-112">Element with a sequence of child elements</span></span>  
  
6. <span data-ttu-id="25bdb-113">Alt öğeler ve öznitelikler dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-113">Element with a sequence of child elements and attributes</span></span>  
  
7. <span data-ttu-id="25bdb-114">Alt öğelerin seçim dizisine sahip öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-114">Element with a sequence of choices of child elements</span></span>  
  
8. <span data-ttu-id="25bdb-115">Alt öğe ve özniteliklerin bir dizi seçimi olan öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-115">Element with a sequence of choices of child elements and attributes</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25bdb-116">Tüm `complexType` Bildirimler anonim türler olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="25bdb-116">All `complexType` declarations are inferred as anonymous types.</span></span> <span data-ttu-id="25bdb-117">Çıkarılan tek genel öğe kök öğesidir; diğer tüm öğeler yereldir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-117">The only global element inferred is the root element; all other elements are local.</span></span>  
  
 <span data-ttu-id="25bdb-118">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-118">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
### <a name="simple-typed-element"></a><span data-ttu-id="25bdb-119">Basit tür belirtilmiş öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-119">Simple Typed Element</span></span>  

 <span data-ttu-id="25bdb-120">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-120">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-121">Kalın öğe, basit tür öğesi için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-121">The bolded element shows the schema inferred for the simple type element.</span></span>  
  
 <span data-ttu-id="25bdb-122">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-122">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-123">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-123">XML</span></span>|<span data-ttu-id="25bdb-124">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-124">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a><span data-ttu-id="25bdb-125">Boş öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-125">Empty Element</span></span>  

 <span data-ttu-id="25bdb-126">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-126">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-127">Kalın öğe, boş öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-127">The bolded element shows the schema inferred for the empty element.</span></span>  
  
 <span data-ttu-id="25bdb-128">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-128">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-129">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-129">XML</span></span>|<span data-ttu-id="25bdb-130">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-130">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a><span data-ttu-id="25bdb-131">Öznitelikleri olan boş öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-131">Empty Element with Attributes</span></span>  

 <span data-ttu-id="25bdb-132">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-132">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-133">Kalın öğeler, özniteliklerin bulunduğu boş öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-133">The bolded elements show the schema inferred for the empty element with attributes.</span></span>  
  
 <span data-ttu-id="25bdb-134">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-134">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-135">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-135">XML</span></span>|<span data-ttu-id="25bdb-136">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-136">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a><span data-ttu-id="25bdb-137">Öznitelikleri ve basit Içeriği olan öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-137">Element with Attributes and Simple Content</span></span>  

 <span data-ttu-id="25bdb-138">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-138">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-139">Kalın öğeler, öznitelikleri ve basit içeriği olan bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-139">The bolded elements show the schema inferred for an element with attributes and simple content.</span></span>  
  
 <span data-ttu-id="25bdb-140">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-140">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-141">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-141">XML</span></span>|<span data-ttu-id="25bdb-142">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-142">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a><span data-ttu-id="25bdb-143">Alt öğeleri dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-143">Element with a Sequence of Child Elements</span></span>  

 <span data-ttu-id="25bdb-144">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-144">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-145">Kalın öğeler, alt öğeleri dizisi olan bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-145">The bolded elements show the schema inferred for an element with a sequence of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25bdb-146">Bir öğenin yalnızca bir alt öğesi olsa bile, yine de bir sıra olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-146">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="25bdb-147">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-147">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-148">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-148">XML</span></span>|<span data-ttu-id="25bdb-149">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-149">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a><span data-ttu-id="25bdb-150">Alt öğeler ve öznitelikler dizisi olan öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-150">Element with a Sequence of Child Elements and Attributes</span></span>  

 <span data-ttu-id="25bdb-151">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-151">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-152">Kalın öğeler, alt öğe ve özniteliklerin sırası olan bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-152">The bolded elements show the schema inferred for an element with a sequence of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25bdb-153">Bir öğenin yalnızca bir alt öğesi olsa bile, yine de bir sıra olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-153">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="25bdb-154">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-154">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-155">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-155">XML</span></span>|<span data-ttu-id="25bdb-156">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-156">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a><span data-ttu-id="25bdb-157">Alt öğelerin sırası ve seçimlerine sahip öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-157">Element with a Sequence and Choices of Child Elements</span></span>  

 <span data-ttu-id="25bdb-158">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-158">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-159">Kalın öğeler, bir öğe için gösterilen şemayı bir dizi ve tercih edilen alt öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-159">The bolded elements show the schema inferred for an element with a sequence and choice of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25bdb-160">`maxOccurs`Öğesinin özniteliği, `xs:choice` `"unbounded"` gösterilen şemada olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="25bdb-160">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="25bdb-161">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-161">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-162">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-162">XML</span></span>|<span data-ttu-id="25bdb-163">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-163">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a><span data-ttu-id="25bdb-164">Alt öğe ve özniteliklerin sırası ve seçimi içeren öğe</span><span class="sxs-lookup"><span data-stu-id="25bdb-164">Element with a Sequence and Choice of Child Elements and Attributes</span></span>  

 <span data-ttu-id="25bdb-165">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , YÖNTEMINE XML girişi ve oluşturulan XML şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-165">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="25bdb-166">Kalın öğeler, alt öğe ve özniteliklerin sırası ve seçimi içeren bir öğe için gösterilen şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-166">The bolded elements show the schema inferred for an element with a sequence and choice of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25bdb-167">`maxOccurs`Öğesinin özniteliği, `xs:choice` `"unbounded"` gösterilen şemada olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="25bdb-167">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="25bdb-168">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-168">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="25bdb-169">XML</span><span class="sxs-lookup"><span data-stu-id="25bdb-169">XML</span></span>|<span data-ttu-id="25bdb-170">Şema</span><span class="sxs-lookup"><span data-stu-id="25bdb-170">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a><span data-ttu-id="25bdb-171">Öznitelik Işleme</span><span class="sxs-lookup"><span data-stu-id="25bdb-171">Attribute Processing</span></span>  

 <span data-ttu-id="25bdb-172">Düğüm içinde yeni bir özniteliğe her karşılaşıldığında, bu, ile düğümün çıkarılan tanımına eklenir `use="required"` .</span><span class="sxs-lookup"><span data-stu-id="25bdb-172">Whenever a new attribute is encountered within a node, it is added to the inferred definition of the node with `use="required"`.</span></span> <span data-ttu-id="25bdb-173">Örnekte aynı düğüm bir sonraki sefer olduğunda, çıkarım işlemi geçerli örneğin özniteliklerini zaten çıkartılan olanlarla karşılaştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="25bdb-173">The next time the same node is found in the instance, the inference process will compare attributes of the current instance with the ones already inferred.</span></span> <span data-ttu-id="25bdb-174">Örnekte zaten başka bir görünenler varsa, `use="optional"` öznitelik tanımına eklenir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-174">If some of the already inferred ones are missing in the instance, `use="optional"` is added to the attribute definition.</span></span> <span data-ttu-id="25bdb-175">Yeni öznitelikler ile var olan bildirimlere eklenir `use="optional"` .</span><span class="sxs-lookup"><span data-stu-id="25bdb-175">New attributes are added to existing declarations with `use="optional"`.</span></span>  
  
### <a name="occurrence-constraints"></a><span data-ttu-id="25bdb-176">Oluşum kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="25bdb-176">Occurrence Constraints</span></span>  

 <span data-ttu-id="25bdb-177">Şema çıkarımı işlemi sırasında, `minOccurs` ve `maxOccurs` öznitelikleri, bir şemanın Çıkarsanan bileşenleri için, `"0"` veya `"1"` ve ya da değerleri oluşturulur `"1"` `"unbounded"` .</span><span class="sxs-lookup"><span data-stu-id="25bdb-177">During the schema inference process, the `minOccurs` and `maxOccurs` attributes are generated, for inferred components of a schema, with the values `"0"` or `"1"` and `"1"` or `"unbounded"`.</span></span> <span data-ttu-id="25bdb-178">Değerler `"1"` ve `"unbounded"` yalnızca değerler `"0"` ve `"1"` XML belgesini doğrulayamıyorsa kullanılır (örneğin, `MinOccurs="0"` bir öğeyi doğru bir şekilde açıklamıyorsa, `minOccurs="1"` kullanılır).</span><span class="sxs-lookup"><span data-stu-id="25bdb-178">The values `"1"` and `"unbounded"` are used only when the values `"0"` and `"1"` cannot validate the XML document (for example, if `MinOccurs="0"` does not accurately describe an element, `minOccurs="1"` is used).</span></span>  
  
### <a name="mixed-content"></a><span data-ttu-id="25bdb-179">Karışık Içerik</span><span class="sxs-lookup"><span data-stu-id="25bdb-179">Mixed Content</span></span>  

 <span data-ttu-id="25bdb-180">Bir öğe, karışık içerik içeriyorsa (örneğin, öğelerle birlikte metin oluşturma), bu öznitelik, `mixed="true"` gösterilen karmaşık tür tanımı için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="25bdb-180">If an element contains mixed content (for example text interspersed with elements), the `mixed="true"` attribute is generated for the inferred complex type definition.</span></span>  
  
## <a name="other-node-type-inference-rules"></a><span data-ttu-id="25bdb-181">Diğer düğüm türü çıkarımı kuralları</span><span class="sxs-lookup"><span data-stu-id="25bdb-181">Other Node Type Inference Rules</span></span>  

 <span data-ttu-id="25bdb-182">Aşağıdaki tabloda yönerge, açıklama, varlık başvurusu, CDATA, belge türü ve ad alanı düğümlerini işlemek için çıkarım kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25bdb-182">The following table describes the inference rules for processing instruction, comment, entity reference, CDATA, document type, and namespace nodes.</span></span>  
  
|<span data-ttu-id="25bdb-183">Düğüm türü</span><span class="sxs-lookup"><span data-stu-id="25bdb-183">Node Type</span></span>|<span data-ttu-id="25bdb-184">Çeviri</span><span class="sxs-lookup"><span data-stu-id="25bdb-184">Translation</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25bdb-185">İşlem yönergesi</span><span class="sxs-lookup"><span data-stu-id="25bdb-185">Processing instruction</span></span>|<span data-ttu-id="25bdb-186">LIP.</span><span class="sxs-lookup"><span data-stu-id="25bdb-186">Ignored.</span></span>|  
|<span data-ttu-id="25bdb-187">Yorum</span><span class="sxs-lookup"><span data-stu-id="25bdb-187">Comment</span></span>|<span data-ttu-id="25bdb-188">LIP.</span><span class="sxs-lookup"><span data-stu-id="25bdb-188">Ignored.</span></span>|  
|<span data-ttu-id="25bdb-189">Varlık başvurusu</span><span class="sxs-lookup"><span data-stu-id="25bdb-189">Entity reference</span></span>|<span data-ttu-id="25bdb-190"><xref:System.Xml.Schema.XmlSchemaInference>Sınıf, varlık başvurularını işlemez.</span><span class="sxs-lookup"><span data-stu-id="25bdb-190">The <xref:System.Xml.Schema.XmlSchemaInference> class does not handle entity references.</span></span> <span data-ttu-id="25bdb-191">Bir XML belgesi varlık başvuruları içeriyorsa, varlıkları genişleten bir okuyucu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25bdb-191">If an XML document contains entity references, you need to use a reader that expands the entities.</span></span> <span data-ttu-id="25bdb-192">Örneğin, <xref:System.Xml.XmlTextReader> <xref:System.Xml.XmlTextReader.EntityHandling%2A> özelliğini bir parametre olarak ayarlanmış şekilde bir ile geçirebilirsiniz <xref:System.Xml.EntityHandling.ExpandEntities> .</span><span class="sxs-lookup"><span data-stu-id="25bdb-192">For example, you can pass an <xref:System.Xml.XmlTextReader> with the <xref:System.Xml.XmlTextReader.EntityHandling%2A> property set to <xref:System.Xml.EntityHandling.ExpandEntities> as a parameter.</span></span> <span data-ttu-id="25bdb-193">Varlık başvurularına karşılaşılırsa ve okuyucu varlıkları genişletmezse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25bdb-193">If entity references are encountered and the reader does not expand entities, an exception is throw.</span></span>|  
|<span data-ttu-id="25bdb-194">CDATA</span><span class="sxs-lookup"><span data-stu-id="25bdb-194">CDATA</span></span>|<span data-ttu-id="25bdb-195">`<![CDATA[ … ]]`XML belgesindeki tüm bölümler, olarak algılanır `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="25bdb-195">Any `<![CDATA[ … ]]` sections in an XML document will be inferred as `xs:string`.</span></span>|  
|<span data-ttu-id="25bdb-196">Belge türü</span><span class="sxs-lookup"><span data-stu-id="25bdb-196">Document type</span></span>|<span data-ttu-id="25bdb-197">LIP.</span><span class="sxs-lookup"><span data-stu-id="25bdb-197">Ignored.</span></span>|  
|<span data-ttu-id="25bdb-198">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="25bdb-198">Namespaces</span></span>|<span data-ttu-id="25bdb-199">LIP.</span><span class="sxs-lookup"><span data-stu-id="25bdb-199">Ignored.</span></span>|  
  
 <span data-ttu-id="25bdb-200">Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](inferring-schemas-from-xml-documents.md)yapma.</span><span class="sxs-lookup"><span data-stu-id="25bdb-200">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bdb-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25bdb-201">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="25bdb-202">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="25bdb-202">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="25bdb-203">XML Şemasından Çıkarım Yapma</span><span class="sxs-lookup"><span data-stu-id="25bdb-203">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="25bdb-204">XML Belgelerinden Şema Çıkarımı Yapma</span><span class="sxs-lookup"><span data-stu-id="25bdb-204">Inferring Schemas from XML Documents</span></span>](inferring-schemas-from-xml-documents.md)
- [<span data-ttu-id="25bdb-205">Basit Türlerin Çıkarımını Yapma Kuralları</span><span class="sxs-lookup"><span data-stu-id="25bdb-205">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
