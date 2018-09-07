---
title: XML şemasından (XSD) DataSet ilişkileri oluşturma
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 7c73dcec3d23b094436791af6649de83b9eacad9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076338"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="a6971-102">XML şemasından (XSD) DataSet ilişkileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6971-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="a6971-103">İçinde bir <xref:System.Data.DataSet>, bir üst-alt ilişkisi oluşturarak iki veya daha fazla sütunu arasında bir ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6971-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="a6971-104">Göstermek için üç yol vardır bir **veri kümesi** ilişkisi içinde bir XML Şeması Tanım Dili (XSD) şeması:</span><span class="sxs-lookup"><span data-stu-id="a6971-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="a6971-105">Karmaşık iç içe geçmiş türler belirtin.</span><span class="sxs-lookup"><span data-stu-id="a6971-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="a6971-106">Kullanım **msdata:Relationship** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="a6971-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="a6971-107">Belirtin bir **xs:keyref** olmadan **msdata:ConstraintOnly** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="a6971-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="a6971-108">Karmaşık iç içe geçmiş türler</span><span class="sxs-lookup"><span data-stu-id="a6971-108">Nested Complex Types</span></span>  
 <span data-ttu-id="a6971-109">İç içe geçmiş bir karmaşık tür tanımlarını bir şemadaki öğelerin üst-alt ilişkileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6971-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="a6971-110">Aşağıdaki XML Şeması parçası gösteren **OrderDetail** bir alt öğesidir **sipariş** öğesi.</span><span class="sxs-lookup"><span data-stu-id="a6971-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="a6971-111">XML Şeması eşleme işlemi tablolarında oluşturur **veri kümesi** karşılık gelen şema karmaşık iç içe geçmiş türleri için.</span><span class="sxs-lookup"><span data-stu-id="a6971-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="a6971-112">Üst öğe olarak kullanılan ek sütunlar da oluşturur**-** oluşturulan tablolar için alt sütunlar.</span><span class="sxs-lookup"><span data-stu-id="a6971-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="a6971-113">Bu üst Not**-** alt sütunlar, birincil anahtar/yabancı anahtar kısıtlamalarını belirtmekle aynı değil ilişkileri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a6971-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="a6971-114">MSDATA:Relationship ek açıklaması</span><span class="sxs-lookup"><span data-stu-id="a6971-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="a6971-115">**Msdata:Relationship** ek açıklama, iç içe yerleştirilmiş şema öğeleri arasında üst-alt ilişkileri açıkça belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6971-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="a6971-116">Aşağıdaki örnek, yapısını gösterir. **ilişki** öğesi.</span><span class="sxs-lookup"><span data-stu-id="a6971-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="a6971-117">Özniteliklerini **msdata:Relationship** ek açıklamayı tanımlamak ilgili olarak üst-alt ilişkisinde, de öğeleri **parentkey** ve **childkey** öğeler ve öznitelikler ilişkide bulunan.</span><span class="sxs-lookup"><span data-stu-id="a6971-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="a6971-118">Eşleme işlemi içinde tablolar oluşturmak için bu bilgileri kullanır. **veri kümesi** ve bu tablolar arasındaki birincil anahtarı/yabancı anahtar ilişkisi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="a6971-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="a6971-119">Örneğin, aşağıdaki şema parçası belirtir **sipariş** ve **OrderDetail** öğeleri aynı düzeyde (iç içe olmayan).</span><span class="sxs-lookup"><span data-stu-id="a6971-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="a6971-120">Şemayı belirtir bir **msdata:Relationship** bu iki öğe arasındaki üst-alt ilişkisi belirten açıklama.</span><span class="sxs-lookup"><span data-stu-id="a6971-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="a6971-121">Bu durumda, açık bir ilişkisi kullanılarak belirtilmelidir **msdata:Relationship** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="a6971-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="a6971-122">Eşleme işlemi kullanır **ilişki** arasında üst-alt ilişkisi oluşturmak için öğe **OrderNumber** sütununda **sipariş** tablo ve **OrderNo** sütununda **OrderDetail** tablosundaki **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="a6971-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="a6971-123">Eşleme işlemi yalnızca ilişkiyi belirtir. birincil anahtarı/yabancı anahtar kısıtlamalarını ilişkisel veritabanları gibi otomatik olarak kısıtlamalardan değerleri bu sütunlarda belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="a6971-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="a6971-124">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a6971-124">In This Section</span></span>  
 [<span data-ttu-id="a6971-125">İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="a6971-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="a6971-126">Örtük olarak oluşturulan ilişkileri ve kısıtlamaları açıklar bir **veri kümesi** , iç içe öğelerin karşılaştı içinde XML şeması.</span><span class="sxs-lookup"><span data-stu-id="a6971-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="a6971-127">İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="a6971-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="a6971-128">Açıkça ilişkileri kümesinde açıklar bir **veri kümesi** XML Şeması iç içe geçmiş öğe.</span><span class="sxs-lookup"><span data-stu-id="a6971-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="a6971-129">İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme</span><span class="sxs-lookup"><span data-stu-id="a6971-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="a6971-130">İlişkiler oluşturmayı açıklar bir **veri kümesi** iç içe yerleştirilmiş bir XML Şeması öğeleri arasında.</span><span class="sxs-lookup"><span data-stu-id="a6971-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="a6971-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a6971-131">Related Sections</span></span>  
 [<span data-ttu-id="a6971-132">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="a6971-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="a6971-133">İlişkisel yapısını veya şema biri açıklar bir **veri kümesi** XML Şeması Tanım Dili (XSD) şemaya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a6971-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="a6971-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="a6971-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="a6971-135">Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="a6971-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6971-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6971-136">See Also</span></span>  
 [<span data-ttu-id="a6971-137">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a6971-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
