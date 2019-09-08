---
title: İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: f4b1b9e45f0cda976719b991c336463e0af05f12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784443"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="e3fb6-102">İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="e3fb6-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="e3fb6-103">Bir XML şeması tanım dili (XSD) şeması, bir diğeri içinde iç içe geçmiş karmaşık türlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="e3fb6-104">Bu durumda, eşleme işlemi varsayılan eşlemeyi uygular ve içinde <xref:System.Data.DataSet>aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e3fb6-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="e3fb6-105">Karmaşık türlerin her biri için bir tablo (üst ve alt).</span><span class="sxs-lookup"><span data-stu-id="e3fb6-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="e3fb6-106">Üst öğede benzersiz bir kısıtlama yoksa, TableName *_ID*adlı tablo tanımı başına bir ek birincil anahtar sütunu, *TableName* , üst tablonun adıdır.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="e3fb6-107">Birincil anahtar olarak ek sütunu tanımlayan üst tabloda birincil anahtar kısıtlaması ( **IsPrimaryKey** özelliği **true**olarak ayarlanarak).</span><span class="sxs-lookup"><span data-stu-id="e3fb6-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="e3fb6-108">Kısıtlama, 1, 2\# , \# 3 vb. olduğu kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="e3fb6-109">Örneğin, ilk kısıtlamanın varsayılan adı Constraint1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="e3fb6-110">Üst tablonun birincil anahtarına başvuran yabancı anahtar olarak ek sütunu tanımlayan alt tablodaki yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="e3fb6-111">Kısıtlama *ParentTable_ChildTable* olarak adlandırılır; burada *ParentTable* üst tablonun adı ve *ChildTable* ise alt tablonun adıdır.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="e3fb6-112">Üst ve alt tablolar arasındaki bir veri ilişkisi.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="e3fb6-113">Aşağıdaki örnek, **OrderDetail** 'in **sıra**alt öğesi olduğu bir şemayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="e3fb6-114">XML Şeması eşleme işlemi, **veri kümesinde**aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e3fb6-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="e3fb6-115">Bir **Order** ve **OrderDetail** tablosu.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="e3fb6-116">**Order** tablosundaki benzersiz bir kısıtlama.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="e3fb6-117">**IsPrimaryKey** özelliğinin **true**olarak ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="e3fb6-118">**OrderDetail** tablosundaki yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- <span data-ttu-id="e3fb6-119">**Order** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="e3fb6-120">**Order** ve **OrderDetail** öğeleri şemada iç içe yerleştirilmiş olduğundan, bu ilişkinin **iç içe geçmiş** özelliği **true** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e3fb6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3fb6-121">See also</span></span>

- [<span data-ttu-id="e3fb6-122">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3fb6-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="e3fb6-123">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e3fb6-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="e3fb6-124">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e3fb6-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
