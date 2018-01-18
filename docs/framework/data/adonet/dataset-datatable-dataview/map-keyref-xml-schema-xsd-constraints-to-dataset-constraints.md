---
title: "Harita keyref DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e364efe0856a5291fc8157ef6ab185c2438a3347
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="dd151-102">Harita keyref DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="dd151-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="dd151-103">**Keyref** öğesi bir belgedeki öğeler arasında bağlantı kurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd151-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="dd151-104">Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisi için benzer.</span><span class="sxs-lookup"><span data-stu-id="dd151-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="dd151-105">Bir şema belirtiyorsa **keyref** öğesi, öğenin karşılık gelen bir yabancı anahtar kısıtlaması tablolardaki sütunlarda şema eşleme işlemi sırasında dönüştürülür <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="dd151-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="dd151-106">Varsayılan olarak, **keyref** öğesi de oluşturur bir ilişki ile **ParentTable**, **geldiği**, **ParentColumn**ve  **ChildColumn** özellikler üzerinde ilişkisi belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="dd151-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="dd151-107">Aşağıdaki tabloda ana hatlarını **msdata** içinde belirtebilirsiniz öznitelikleri **keyref** öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd151-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="dd151-108">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="dd151-108">Attribute name</span></span>|<span data-ttu-id="dd151-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd151-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="dd151-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="dd151-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="dd151-111">Varsa **ConstraintOnly = "true"** belirtilen **keyref** schema öğesinde, bir kısıtlama oluşturuldu, ancak hiçbir ilişkisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dd151-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="dd151-112">Bu öznitelik belirtilmediğinde (veya ayarlamak **False**), kısıtlamayı ve ilişki oluşturulan **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="dd151-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="dd151-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="dd151-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="dd151-114">Varsa **ConstraintName** özniteliği belirtilmezse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd151-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="dd151-115">Aksi takdirde, **adı** özniteliği **keyref** schema öğesinde sağlar ve kısıtlama adını **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="dd151-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="dd151-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="dd151-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="dd151-117">Varsa **UpdateRule** özniteliği belirtilen **keyref** schema öğesinde değerini atanması **UpdateRule** kısıtlaması özelliğinde  **Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="dd151-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="dd151-118">Aksi takdirde **UpdateRule** özelliği ayarlanmış **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="dd151-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="dd151-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="dd151-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="dd151-120">Varsa **DeleteRule** özniteliği belirtilen **keyref** schema öğesinde değerini atanması **DeleteRule** kısıtlaması özelliğinde  **Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="dd151-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="dd151-121">Aksi takdirde **DeleteRule** özelliği ayarlanmış **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="dd151-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="dd151-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="dd151-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="dd151-123">Varsa **AcceptRejectRule** özniteliği belirtilen **keyref** schema öğesinde değerini atanması **AcceptRejectRule** kısıtlamasıözelliği **Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="dd151-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="dd151-124">Aksi takdirde **AcceptRejectRule** özelliği ayarlanmış **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="dd151-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="dd151-125">Aşağıdaki örnek belirten bir şema içeriyor **anahtar** ve **keyref** arasındaki ilişkileri **OrderNumber** alt öğesi olan **sırası**  öğesi ve **OrderNo** alt öğesi olan **OrderDetail** öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd151-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="dd151-126">Örnekte, **OrderNumber** alt öğesi olan **OrderDetail** öğesi başvurduğu **OrderNo** anahtar alt öğesi olan **sipariş**öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd151-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="dd151-127">Aşağıdaki XML Şeması Tanım Dili (XSD) şema eşleme işlemi üreten **DataSet** iki tablo ile:</span><span class="sxs-lookup"><span data-stu-id="dd151-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="dd151-128">Ayrıca, **DataSet** aşağıdaki kısıtlamalar tanımlar:</span><span class="sxs-lookup"><span data-stu-id="dd151-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
-   <span data-ttu-id="dd151-129">Benzersiz bir kısıtlama **sipariş** tablo.</span><span class="sxs-lookup"><span data-stu-id="dd151-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   <span data-ttu-id="dd151-130">Arasında bir ilişki **sipariş** ve **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="dd151-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="dd151-131">**İç içe** özelliği ayarlanmış **False** iki öğe şemada iç içe değil çünkü.</span><span class="sxs-lookup"><span data-stu-id="dd151-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   <span data-ttu-id="dd151-132">Bir yabancı anahtar kısıtlaması **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="dd151-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dd151-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd151-133">See Also</span></span>  
 [<span data-ttu-id="dd151-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="dd151-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="dd151-135">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd151-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="dd151-136">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="dd151-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
