---
title: Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 611322065a4df53d1a3149ef4e1ca5592f149081
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203444"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="84435-102">Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="84435-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="84435-103">**Keyref** öğesi bir belge içindeki öğeler arasında bağlantı kurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="84435-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="84435-104">Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="84435-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="84435-105">Bir şema **keyref** öğesini belirtiyorsa, öğesi şema eşleme işlemi sırasında, <xref:System.Data.DataSet>tablolarındaki sütunlarda karşılık gelen bir yabancı anahtar kısıtlamasına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="84435-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="84435-106">Varsayılan olarak, **keyref** öğesi ilişki üzerinde belirtilen **ParentTable**, **ChildTable**, **ParentColumn**ve **ChildColumn** özellikleriyle da bir ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="84435-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="84435-107">Aşağıdaki tabloda, **keyref** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="84435-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="84435-108">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="84435-108">Attribute name</span></span>|<span data-ttu-id="84435-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84435-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="84435-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="84435-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="84435-111">Şemada **keyref** öğesinde **ConstraintOnly = "true"** belirtilirse, bir kısıtlama oluşturulur, ancak ilişki oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="84435-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="84435-112">Bu öznitelik belirtilmemişse (veya **false**olarak ayarlanırsa), hem kısıtlama hem de Ilişki **veri kümesinde**oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="84435-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="84435-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="84435-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="84435-114">**ConstraintName** özniteliği belirtilmişse, değeri kısıtlamanın adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84435-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="84435-115">Aksi takdirde, şemadaki **keyref** öğesinin **Name** özniteliği, **veri kümesinde**kısıtlama adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="84435-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="84435-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="84435-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="84435-117">Şemadaki **keyref** öğesinde **UpdateRule** özniteliği belirtilmişse, değeri **veri kümesindeki** **UpdateRule** kısıtlama özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="84435-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="84435-118">Aksi takdirde **UpdateRule** özelliği **Cascade**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="84435-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="84435-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="84435-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="84435-120">Şemadaki **keyref** öğesinde **DeleteRule** özniteliği belirtilmişse, değeri **veri kümesindeki** **DeleteRule** kısıtlama özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="84435-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="84435-121">Aksi takdirde, **DeleteRule** özelliği **Cascade**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="84435-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="84435-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="84435-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="84435-123">Bir şemadaki **keyref** öğesinde **AcceptRejectRule** özniteliği belirtilmişse, değeri **veri kümesindeki** **AcceptRejectRule** kısıtlama özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="84435-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="84435-124">Aksi takdirde **AcceptRejectRule** özelliği **none**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="84435-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="84435-125">Aşağıdaki örnek, **Order** öğesinin **OrderNumber** alt öğesi ve OrderNo alt öğesi ile **OrderDetail** arasındaki **anahtar** ve **keyref** ilişkilerini belirten bir şema içerir dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="84435-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="84435-126">Örnekte, **OrderDetail** öğesinin **OrderNumber** alt öğesi **Order** öğesinin **OrderNo** anahtar alt öğesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="84435-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="84435-127">XML şeması tanım dili (XSD) şema eşleme işlemi aşağıdaki **veri kümesini** iki tabloyla üretir:</span><span class="sxs-lookup"><span data-stu-id="84435-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="84435-128">Ayrıca, **veri kümesi** aşağıdaki kısıtlamaları tanımlar:</span><span class="sxs-lookup"><span data-stu-id="84435-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="84435-129">**Order** tablosundaki benzersiz bir kısıtlama.</span><span class="sxs-lookup"><span data-stu-id="84435-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="84435-130">**Order** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="84435-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="84435-131">**Iç içe** geçmiş özelliği **false** olarak ayarlanır çünkü iki öğe şemada iç içe değildir.</span><span class="sxs-lookup"><span data-stu-id="84435-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
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
  
- <span data-ttu-id="84435-132">**OrderDetail** tablosundaki yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="84435-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="84435-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84435-133">See also</span></span>

- [<span data-ttu-id="84435-134">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="84435-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="84435-135">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="84435-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="84435-136">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="84435-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
