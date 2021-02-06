---
description: 'Daha fazla bilgi edinin: Iç Içe geçmiş şema öğeleri arasında örtük Ilişkileri eşleme'
title: İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 418dd1210674b2c592cf96c6d369bc43f8dcab9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652022"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="cef91-103">İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="cef91-103">Map Implicit Relations Between Nested Schema Elements</span></span>

<span data-ttu-id="cef91-104">Bir XML şeması tanım dili (XSD) şeması, bir diğeri içinde iç içe geçmiş karmaşık türlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="cef91-104">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="cef91-105">Bu durumda, eşleme işlemi varsayılan eşlemeyi uygular ve içinde aşağıdakileri oluşturur <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="cef91-105">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="cef91-106">Karmaşık türlerin her biri için bir tablo (üst ve alt).</span><span class="sxs-lookup"><span data-stu-id="cef91-106">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="cef91-107">Üst öğede benzersiz bir kısıtlama yoksa, *TableName adlı tablo* tanımı başına bir ek birincil anahtar sütunu _Id, *TableName* , üst tablonun adıdır.</span><span class="sxs-lookup"><span data-stu-id="cef91-107">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName* _Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="cef91-108">Birincil anahtar olarak ek sütunu tanımlayan üst tabloda birincil anahtar kısıtlaması ( **IsPrimaryKey** özelliği **true** olarak ayarlanarak).</span><span class="sxs-lookup"><span data-stu-id="cef91-108">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="cef91-109">Kısıtlama, \# \# 1, 2, 3 vb. olduğu kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="cef91-109">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="cef91-110">Örneğin, ilk kısıtlamanın varsayılan adı Constraint1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cef91-110">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="cef91-111">Üst tablonun birincil anahtarına başvuran yabancı anahtar olarak ek sütunu tanımlayan alt tablodaki yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="cef91-111">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="cef91-112">Kısıtlama *ParentTable_ChildTable* adlandırılır; burada *ParentTable* üst tablonun adı ve *ChildTable* ise alt tablonun adıdır.</span><span class="sxs-lookup"><span data-stu-id="cef91-112">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="cef91-113">Üst ve alt tablolar arasındaki bir veri ilişkisi.</span><span class="sxs-lookup"><span data-stu-id="cef91-113">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="cef91-114">Aşağıdaki örnek, **OrderDetail** 'in **sıra** alt öğesi olduğu bir şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cef91-114">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="cef91-115">XML Şeması eşleme işlemi, **veri kümesinde** aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="cef91-115">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="cef91-116">Bir **Order** ve **OrderDetail** tablosu.</span><span class="sxs-lookup"><span data-stu-id="cef91-116">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="cef91-117">**Order** tablosundaki benzersiz bir kısıtlama.</span><span class="sxs-lookup"><span data-stu-id="cef91-117">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="cef91-118">**IsPrimaryKey** özelliğinin **true** olarak ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cef91-118">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="cef91-119">**OrderDetail** tablosundaki yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="cef91-119">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="cef91-120">**Order** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="cef91-120">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="cef91-121">**Order** ve **OrderDetail** öğeleri şemada iç içe yerleştirilmiş olduğundan, bu ilişkinin **iç içe geçmiş** özelliği **true** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cef91-121">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cef91-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cef91-122">See also</span></span>

- [<span data-ttu-id="cef91-123">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cef91-123">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="cef91-124">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="cef91-124">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="cef91-125">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cef91-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
