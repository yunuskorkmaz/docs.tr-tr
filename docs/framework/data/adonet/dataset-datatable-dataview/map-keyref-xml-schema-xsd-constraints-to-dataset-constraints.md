---
title: Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150889"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="ba541-102">Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="ba541-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="ba541-103">**Keyref** öğesi, belge içindeki öğeler arasında bağlantılar kurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba541-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="ba541-104">Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisine benzer.</span><span class="sxs-lookup"><span data-stu-id="ba541-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="ba541-105">Şema **keyref** öğesini belirtirse, schema eşleme işlemi sırasında öğe tablolardaki sütunlarda karşılık gelen yabancı <xref:System.Data.DataSet>anahtar kısıtlamasına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ba541-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ba541-106">Varsayılan olarak, **keyref** öğesi de bir ilişki oluşturur, **ParentTable**ile, **ChildTable**, Üst Sütun , ve **ChildColumn**özellikleri ilişki üzerinde belirtilen. **ChildColumn**</span><span class="sxs-lookup"><span data-stu-id="ba541-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="ba541-107">Aşağıdaki tabloda **keyref** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ba541-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="ba541-108">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="ba541-108">Attribute name</span></span>|<span data-ttu-id="ba541-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba541-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ba541-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="ba541-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="ba541-111">**ConstraintOnly="true"** şemadaki **keyref** öğesinde belirtilirse, bir kısıtlama oluşturulur, ancak ilişki oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="ba541-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="ba541-112">Bu öznitelik belirtilmemişse (veya **False**olarak ayarlanmışsa), hem kısıtlama hem de ilişki **DataSet'te**oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ba541-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="ba541-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="ba541-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="ba541-114">**ConstraintName** özniteliği belirtilirse, değeri kısıtlamanın adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba541-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="ba541-115">Aksi takdirde, şemadaki **keyref** öğesinin **ad** özniteliği **DataSet'teki**kısıtlama adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba541-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="ba541-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="ba541-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="ba541-117">Şemadaki **keyref** öğesinde **UpdateRule** özniteliği belirtilirse, değeri **DataSet'teki** **UpdateRule** kısıtlama özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="ba541-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="ba541-118">Aksi takdirde **UpdateRule** özelliği **Basamaklı**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba541-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="ba541-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="ba541-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="ba541-120">Şemadaki **keyref** öğesinde **DeleteRule** özniteliği belirtilirse, değeri **DataSet'teki** **DeleteRule** kısıtlama özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="ba541-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="ba541-121">Aksi takdirde **DeleteRule** özelliği **Basamaklı**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba541-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="ba541-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="ba541-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="ba541-123">**AcceptRejectRule** özniteliği şemadaki **keyref** öğesinde belirtilirse, değeri **DataSet'teki** **AcceptRejectRule** kısıtlama özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="ba541-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="ba541-124">Aksi takdirde **AcceptRejectRule** özelliği **Yok**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba541-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="ba541-125">Aşağıdaki örnek, Sipariş **öğesinin** **OrderNumber** alt öğesi ile **OrderDetail** öğesinin **OrderNo** alt öğesi arasındaki **anahtar** ve **keyref** ilişkilerini belirten bir şema içerir.</span><span class="sxs-lookup"><span data-stu-id="ba541-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="ba541-126">Örnekte, **OrderDetail** öğesinin **OrderNumber** alt öğesi, **Sipariş** öğesinin **OrderNo** anahtar alt öğesini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="ba541-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="ba541-127">XML Şema tanım dili (XSD) şema eşleme işlemi iki tabloile aşağıdaki **DataSet** üretir:</span><span class="sxs-lookup"><span data-stu-id="ba541-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="ba541-128">Buna ek olarak, **DataSet** aşağıdaki kısıtlamaları tanımlar:</span><span class="sxs-lookup"><span data-stu-id="ba541-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="ba541-129">**Sipariş** tablosunda benzersiz bir kısıtlama.</span><span class="sxs-lookup"><span data-stu-id="ba541-129">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="ba541-130">**Sipariş** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="ba541-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="ba541-131">İki öğe şemada iç içe olmadığından **İç Içe Geçen** özellik **False** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba541-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="ba541-132">**OrderDetail** tablosunda yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="ba541-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ba541-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba541-133">See also</span></span>

- [<span data-ttu-id="ba541-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="ba541-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="ba541-135">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba541-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="ba541-136">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ba541-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
