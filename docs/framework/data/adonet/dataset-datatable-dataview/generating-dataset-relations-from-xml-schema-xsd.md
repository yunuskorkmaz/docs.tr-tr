---
title: "DataSet ilişkileri XML Schema (XSD) oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 916b9ad24c2ae2334635760a520116b4c19df314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="d77ee-102">DataSet ilişkileri XML Schema (XSD) oluşturma</span><span class="sxs-lookup"><span data-stu-id="d77ee-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="d77ee-103">İçinde bir <xref:System.Data.DataSet>, bir üst-alt ilişkisi oluşturarak iki veya daha fazla sütun arasında bir ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d77ee-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="d77ee-104">Göstermek için üç yolu bir **DataSet** ilişkisi bir XML Şeması Tanım Dili (XSD) şeması içinde:</span><span class="sxs-lookup"><span data-stu-id="d77ee-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="d77ee-105">İç içe geçmiş karmaşık türler belirtin.</span><span class="sxs-lookup"><span data-stu-id="d77ee-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="d77ee-106">Kullanım **msdata:Relationship** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="d77ee-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="d77ee-107">Belirtin bir **xs:keyref** olmadan **msdata:ConstraintOnly** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="d77ee-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="d77ee-108">İç içe geçmiş karmaşık türler</span><span class="sxs-lookup"><span data-stu-id="d77ee-108">Nested Complex Types</span></span>  
 <span data-ttu-id="d77ee-109">Bir şemadaki iç içe geçmiş karmaşık tür tanımları öğelerin üst-alt ilişkisi belirtin.</span><span class="sxs-lookup"><span data-stu-id="d77ee-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="d77ee-110">Aşağıdaki XML Şeması parça gösterir **OrderDetail** bir alt öğesi olan **sipariş** öğesi.</span><span class="sxs-lookup"><span data-stu-id="d77ee-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="d77ee-111">XML şema eşleme işlemi tablolarda oluşturur **DataSet** , karşılık gelen şema iç içe geçmiş karmaşık türler için.</span><span class="sxs-lookup"><span data-stu-id="d77ee-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="d77ee-112">Ayrıca üst öğe olarak kullanılan ek sütunlar oluşturur**-**alt sütunları oluşturulan tablolar için.</span><span class="sxs-lookup"><span data-stu-id="d77ee-112">It also creates additional columns that are used as parent**-**child columns for the generated tables.</span></span> <span data-ttu-id="d77ee-113">Bu üst Not**-**alt sütunları birincil anahtarı/yabancı anahtar kısıtlamaları belirtme aynı olmayan ilişkiler belirtin.</span><span class="sxs-lookup"><span data-stu-id="d77ee-113">Note that these parent**-**child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="d77ee-114">MSDATA:Relationship ek açıklaması</span><span class="sxs-lookup"><span data-stu-id="d77ee-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="d77ee-115">**Msdata:Relationship** ek açıklama açıkça şemadaki değil iç içe öğeler arasındaki üst-alt ilişkileri belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="d77ee-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="d77ee-116">Aşağıdaki örnek, yapısını gösterir **ilişki** öğesi.</span><span class="sxs-lookup"><span data-stu-id="d77ee-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="d77ee-117">Özniteliklerini **msdata:Relationship** ek açıklama ilgili olarak üst-alt ilişkisinde, de öğeleri tanımlamak **parentkey** ve **childkey** öğeleri ve özniteliklerinin ilişkide bulunan.</span><span class="sxs-lookup"><span data-stu-id="d77ee-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="d77ee-118">Eşleme işlemini, tablolar oluşturmak için bu bilgileri kullanır. **DataSet** ve bu tablolar arasındaki birincil anahtarı/yabancı anahtar ilişkisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d77ee-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="d77ee-119">Örneğin, aşağıdaki şema parça belirtir **sipariş** ve **OrderDetail** öğeleri aynı düzeyde (iç içe değil).</span><span class="sxs-lookup"><span data-stu-id="d77ee-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="d77ee-120">Şema belirten bir **msdata:Relationship** ek açıklama bu iki öğenin üst-alt ilişkisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d77ee-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="d77ee-121">Bu durumda, açık bir ilişkisi kullanılarak belirtilmelidir **msdata:Relationship** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="d77ee-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="d77ee-122">Eşleme işlemini kullanan **ilişki** öğesi bir üst-alt ilişkisi oluşturmak için **OrderNumber** sütununda **sipariş** tablo ve **OrderNo** sütununda **OrderDetail** tablosundaki **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d77ee-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="d77ee-123">Eşleme işlemini yalnızca ilişki belirtir; birincil anahtar/yabancı anahtar kısıtlamaları ilişkisel veritabanları gibi otomatik olarak değerlerinde kısıtlamalar bu sütunlarda belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="d77ee-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="d77ee-124">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d77ee-124">In This Section</span></span>  
 [<span data-ttu-id="d77ee-125">İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="d77ee-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="d77ee-126">Kısıtlamalar ve örtük olarak oluşturulmuş ilişkileri açıklar bir **DataSet** zaman iç içe öğelerin karşılaştı XML şeması.</span><span class="sxs-lookup"><span data-stu-id="d77ee-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="d77ee-127">İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="d77ee-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="d77ee-128">Açıkça ilişkileri nasıl ayarlanacağını açıklar bir **DataSet** XML Şeması iç içe geçmiş öğe.</span><span class="sxs-lookup"><span data-stu-id="d77ee-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="d77ee-129">İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme</span><span class="sxs-lookup"><span data-stu-id="d77ee-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="d77ee-130">İlişkilerine oluşturmayı açıklar bir **DataSet** değil iç içe XML şema öğeleri arasında.</span><span class="sxs-lookup"><span data-stu-id="d77ee-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="d77ee-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d77ee-131">Related Sections</span></span>  
 [<span data-ttu-id="d77ee-132">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="d77ee-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d77ee-133">İlişkisel yapısı veya şema açıklayan bir **veri kümesi** XML Şeması Tanım Dili (XSD) şemadan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d77ee-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="d77ee-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="d77ee-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d77ee-135">Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML şema öğeleri açıklayan bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d77ee-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77ee-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d77ee-136">See Also</span></span>  
 [<span data-ttu-id="d77ee-137">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d77ee-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
