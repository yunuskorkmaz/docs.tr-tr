---
title: XML Şemasından (XSD) DataSet İlişkileri Oluşturma
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 2673280ebb94dcc10c130f3969f3e3250d3706a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198593"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="65c2f-102">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="65c2f-102">Generating DataSet Relations from XML Schema (XSD)</span></span>

<span data-ttu-id="65c2f-103">Bir üzerinde <xref:System.Data.DataSet> üst-alt ilişkisi oluşturarak iki veya daha fazla sütun arasında bir ilişki oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="65c2f-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="65c2f-104">Bir XML şeması tanım dili (XSD) şeması içindeki bir **veri kümesi** ilişkisini göstermenin üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="65c2f-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="65c2f-105">İç içe karmaşık türleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="65c2f-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="65c2f-106">**Msdata: ilişki** ek açıklamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="65c2f-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="65c2f-107">**Msdata: ConstraintOnly** ek açıklaması olmadan **xs: keyref** belirtin.</span><span class="sxs-lookup"><span data-stu-id="65c2f-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="65c2f-108">İç içe karmaşık türler</span><span class="sxs-lookup"><span data-stu-id="65c2f-108">Nested Complex Types</span></span>  

 <span data-ttu-id="65c2f-109">Bir şemadaki iç içe karmaşık tür tanımları, öğelerin üst-alt ilişkilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="65c2f-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="65c2f-110">Aşağıdaki XML şema parçası, **OrderDetail** öğesinin **Order** öğesinin bir alt öğesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="65c2f-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="65c2f-111">XML Şeması eşleme işlemi, **veri kümesinde** , şemadaki iç içe geçmiş karmaşık türlere karşılık gelen tablolar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65c2f-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="65c2f-112">Ayrıca **-** , oluşturulan tablolar için üst alt öğe olarak kullanılan ek sütunlar da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65c2f-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="65c2f-113">Bu üst **-** alt öğe sütunlarının, birincil anahtar/yabancı anahtar kısıtlamalarını belirtmekle aynı olmayan ilişkiler belirttiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="65c2f-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="65c2f-114">msdata: Ilişki ek açıklaması</span><span class="sxs-lookup"><span data-stu-id="65c2f-114">msdata:Relationship Annotation</span></span>  

 <span data-ttu-id="65c2f-115">**Msdata: ilişki** ek açıklaması, şemada iç içe olmayan öğeler arasında üst-alt ilişkileri açıkça belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="65c2f-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="65c2f-116">Aşağıdaki örnek **ilişki** öğesinin yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="65c2f-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="65c2f-117">**Msdata: ilişki** ek açıklaması, üst-alt ilişkisine dahil olan öğeleri ve ayrıca, ilişkili **ParentKey** ve **ChildKey** öğelerini ve özniteliklerini belirler.</span><span class="sxs-lookup"><span data-stu-id="65c2f-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="65c2f-118">Eşleme işlemi bu bilgileri **veri kümesinde** tablolar oluşturmak ve bu tablolar arasında birincil anahtar/yabancı anahtar ilişkisi oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="65c2f-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="65c2f-119">Örneğin, aşağıdaki şema parçası aynı düzeydeki **Order** ve **OrderDetail** öğelerini belirtir (iç içe değil).</span><span class="sxs-lookup"><span data-stu-id="65c2f-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="65c2f-120">Şema, bu iki öğe arasındaki üst-alt ilişkiyi belirten bir **msdata: ilişki** ek açıklaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="65c2f-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="65c2f-121">Bu durumda, **msdata: ilişki** ek açıklaması kullanılarak açık bir ilişki belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="65c2f-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="65c2f-122">Eşleme işlemi **ilişki** öğesini, **Düzen** tablosundaki **OrderNumber** sütunu ve **veri kümesindeki** **OrderDetail** tablosundaki **OrderNo** sütunu arasında bir üst-alt ilişki oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="65c2f-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="65c2f-123">Eşleme işlemi yalnızca ilişkiyi belirtir; ilişkisel veritabanlarındaki birincil anahtar/yabancı anahtar kısıtlamaları gibi, bu sütunlardaki değerlerde otomatik olarak herhangi bir kısıtlama belirtmez.</span><span class="sxs-lookup"><span data-stu-id="65c2f-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="65c2f-124">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="65c2f-124">In This Section</span></span>  

 [<span data-ttu-id="65c2f-125">İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="65c2f-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="65c2f-126">XML şemasında iç içe öğeler ile karşılaşıldığında bir **veri kümesinde** örtük olarak oluşturulan kısıtlamaları ve ilişkileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="65c2f-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="65c2f-127">İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="65c2f-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="65c2f-128">XML şemasında iç içe geçmiş öğeler için bir **veri kümesindeki** ilişkilerin açıkça nasıl ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="65c2f-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="65c2f-129">İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme</span><span class="sxs-lookup"><span data-stu-id="65c2f-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="65c2f-130">Bir **veri kümesinde** iç Içe olmayan xml şema öğeleri arasındaki ilişkilerin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="65c2f-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="65c2f-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="65c2f-131">Related Sections</span></span>  

 [<span data-ttu-id="65c2f-132">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="65c2f-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="65c2f-133">XML şeması tanım dili (XSD) şemasından oluşturulan bir **veri kümesinin** ilişkisel yapısını veya şemasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="65c2f-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="65c2f-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="65c2f-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="65c2f-135">Bir **veri kümesinde**benzersiz ve yabancı anahtar kısıtlamaları oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="65c2f-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c2f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65c2f-136">See also</span></span>

- [<span data-ttu-id="65c2f-137">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="65c2f-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
