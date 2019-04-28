---
title: Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: dcb295aef6d93222e682ef7f720c83963036e795
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607507"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="0814f-102">Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="0814f-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="0814f-103">**Keyref** öğesi bir belge içindeki öğeleri arasında bağlantı kurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0814f-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="0814f-104">Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisi için benzer.</span><span class="sxs-lookup"><span data-stu-id="0814f-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="0814f-105">Bir şema belirtiyorsa **keyref** öğesi, öğenin karşılık gelen bir yabancı anahtar kısıtlaması tablolar sütunlar üzerinde şema eşleme işlemi sırasında dönüştürülür <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0814f-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0814f-106">Varsayılan olarak, **keyref** öğesi ayrıca oluşturur bir ilişki ile **ParentTable**, **geldiği**, **ParentColumn**ve  **ChildColumn** özellikler üzerinde ilişkisi belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="0814f-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="0814f-107">Aşağıdaki tabloda ana hatlarını **msdata** öznitelikleri içinde belirtebileceğiniz **keyref** öğesi.</span><span class="sxs-lookup"><span data-stu-id="0814f-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="0814f-108">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="0814f-108">Attribute name</span></span>|<span data-ttu-id="0814f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0814f-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0814f-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="0814f-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="0814f-111">Varsa **ConstraintOnly = "true"** belirtilen **keyref** şema öğesi, bir kısıtlama oluşturuldu, ancak hiçbir ilişkisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0814f-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="0814f-112">Bu öznitelik belirtilmezse (veya **False**), kısıtlama hem ilişki oluşturulan **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0814f-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="0814f-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="0814f-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="0814f-114">Varsa **ConstraintName** özniteliği belirtilirse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0814f-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="0814f-115">Aksi takdirde, **adı** özniteliği **keyref** şema öğesi sağlar kısıtlama adı **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0814f-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="0814f-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="0814f-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="0814f-117">Varsa **UpdateRule** özniteliği belirtilirse **keyref** şema öğesi, değeri atanır **UpdateRule** kısıtlaması özelliğinde  **Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0814f-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="0814f-118">Aksi takdirde **UpdateRule** özelliği **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="0814f-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="0814f-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="0814f-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="0814f-120">Varsa **DeleteRule** özniteliği belirtilirse **keyref** şema öğesi, değeri atanır **DeleteRule** kısıtlaması özelliğinde  **Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0814f-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="0814f-121">Aksi takdirde **DeleteRule** özelliği **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="0814f-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="0814f-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="0814f-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="0814f-123">Varsa **AcceptRejectRule** özniteliği belirtilirse **keyref** şema öğesi, değeri atanır **AcceptRejectRule** kısıtlamaözelliği **Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0814f-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="0814f-124">Aksi takdirde **AcceptRejectRule** özelliği **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="0814f-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="0814f-125">Aşağıdaki örnek belirten bir şema içeriyor **anahtarı** ve **keyref** arasındaki ilişkileri **OrderNumber** alt öğesi **sırası**  öğesi ve **OrderNo** alt öğesi **OrderDetail** öğesi.</span><span class="sxs-lookup"><span data-stu-id="0814f-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="0814f-126">Örnekte, **OrderNumber** alt öğesi **OrderDetail** öğesi başvurduğu **OrderNo** anahtar alt öğesi **sipariş**öğesi.</span><span class="sxs-lookup"><span data-stu-id="0814f-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="0814f-127">Aşağıdaki XML Şeması Tanım Dili (XSD) şemaya eşleme işlemi üretir **veri kümesi** iki tabloya:</span><span class="sxs-lookup"><span data-stu-id="0814f-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="0814f-128">Ayrıca, **veri kümesi** aşağıdaki kısıtlamalar tanımlar:</span><span class="sxs-lookup"><span data-stu-id="0814f-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="0814f-129">Benzersiz kısıtlama **sipariş** tablo.</span><span class="sxs-lookup"><span data-stu-id="0814f-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="0814f-130">Arasında bir ilişki **sipariş** ve **OrderDetail** tablolar.</span><span class="sxs-lookup"><span data-stu-id="0814f-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="0814f-131">**İç içe** özelliği **False** iki öğe şemasında değil nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="0814f-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
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
  
- <span data-ttu-id="0814f-132">Bir yabancı anahtar kısıtlaması **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="0814f-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0814f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0814f-133">See also</span></span>

- [<span data-ttu-id="0814f-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="0814f-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="0814f-135">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0814f-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="0814f-136">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0814f-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
