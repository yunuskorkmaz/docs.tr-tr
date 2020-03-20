---
title: XML Şemasından (XSD) DataSet İlişkileri Oluşturma
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151136"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="54b63-102">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54b63-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="54b63-103">Bir <xref:System.Data.DataSet>, bir üst-alt ilişkisi oluşturarak iki veya daha fazla sütun arasında bir ilişki oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="54b63-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="54b63-104">Bir XML Şema tanım dili (XSD) şeması içinde bir **DataSet** ilişkisini temsil etmenin üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="54b63-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="54b63-105">İç içe karmaşık türleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="54b63-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="54b63-106">**msdata:İlişki** ek açıklamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="54b63-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="54b63-107">Msdata olmadan bir **xs:keyref** **belirtin:ConstraintOnly** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="54b63-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="54b63-108">İç Içe Karmaşık Türleri</span><span class="sxs-lookup"><span data-stu-id="54b63-108">Nested Complex Types</span></span>  
 <span data-ttu-id="54b63-109">Şemada iç içe yer alan karmaşık tür tanımları, öğelerin üst-alt ilişkilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54b63-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="54b63-110">Aşağıdaki XML Şema **parçası, OrderDetail'ın** **Sipariş** öğesinin alt öğesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54b63-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="54b63-111">XML Şema eşleme işlemi, **DataSet'te** şemadaki iç içe geçen karmaşık türlere karşılık gelen tablolar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b63-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="54b63-112">Ayrıca, oluşturulan tablolar için üst**-** alt sütunolarak kullanılan ek sütunlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b63-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="54b63-113">Bu üst**-** alt sütunların, birincil anahtar/yabancı anahtar kısıtlamalarını belirtmekle aynı olmayan ilişkileri belirtdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="54b63-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="54b63-114">msdata:İlişki Açıklama</span><span class="sxs-lookup"><span data-stu-id="54b63-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="54b63-115">**msdata:İlişki** ek belirti, şemada iç içe geçmemiş öğeler arasındaki üst-alt ilişkilerini açıkça belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="54b63-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="54b63-116">Aşağıdaki örnek, **İlişki** öğesinin yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54b63-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="54b63-117">**msdata'nın öznitelikleri:İlişki** ek açıklama, üst-alt ilişkisinde yer alan öğelerin yanı sıra **ilişkide** yer alan üst anahtar ve **alt anahtar** öğelerini ve öznitelikleritanımlar.</span><span class="sxs-lookup"><span data-stu-id="54b63-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="54b63-118">Eşleme işlemi, Bu bilgileri **DataSet'te** tablo oluşturmak ve bu tablolar arasındaki birincil anahtar/yabancı anahtar ilişkisini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="54b63-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="54b63-119">Örneğin, aşağıdaki şema parçası **Sipariş** ve **OrderDetail** öğelerini aynı düzeyde (iç içe değil) belirtir.</span><span class="sxs-lookup"><span data-stu-id="54b63-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="54b63-120">Şema, bu iki öğe arasındaki üst-alt ilişkisini belirten bir **msdata:İlişki** ek açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54b63-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="54b63-121">Bu durumda, **msdata:İlişki** ek açıklama kullanılarak açık bir ilişki belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="54b63-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="54b63-122">Eşleme işlemi, **Sipariş** tablosundaki **OrderNumber sütunu** ile **DataSet'teki**OrderDetail tablosundaki **OrderNo** sütunu arasında üst-alt ilişki oluşturmak için **İlişki** öğesini kullanır. **OrderNo**</span><span class="sxs-lookup"><span data-stu-id="54b63-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="54b63-123">Eşleme işlemi yalnızca ilişkiyi belirtir; bu sütunlarda değerler üzerinde herhangi bir kısıtlama otomatik olarak belirtmez, ilişkisel veritabanlarında birincil anahtar/yabancı anahtar kısıtlamaları gibi.</span><span class="sxs-lookup"><span data-stu-id="54b63-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="54b63-124">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="54b63-124">In This Section</span></span>  
 [<span data-ttu-id="54b63-125">İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="54b63-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="54b63-126">XML Schema'da iç içe geçmiş öğelerle **karşılaşıldığında, bir DataSet'te** örtülü olarak oluşturulan kısıtlamaları ve ilişkileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="54b63-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="54b63-127">İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="54b63-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="54b63-128">XML Şeması'nda iç içe geçen öğeler için bir **DataSet'teki** ilişkileri açıkça nasıl ayarlayabilirsiniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="54b63-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="54b63-129">İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme</span><span class="sxs-lookup"><span data-stu-id="54b63-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="54b63-130">İç içe geçmemiş XML Şema öğeleri arasında **Bir DataSet'te** nasıl ilişki oluşturulacak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="54b63-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="54b63-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="54b63-131">Related Sections</span></span>  
 [<span data-ttu-id="54b63-132">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="54b63-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="54b63-133">XML Şema tanım dili (XSD) şemasından oluşturulan bir **DataSet'in** ilişkisel yapısını veya şemasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="54b63-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="54b63-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="54b63-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="54b63-135">**DataSet'te**benzersiz ve yabancı anahtar kısıtlamaları oluşturmak için kullanılan XML Şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="54b63-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54b63-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54b63-136">See also</span></span>

- [<span data-ttu-id="54b63-137">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="54b63-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
