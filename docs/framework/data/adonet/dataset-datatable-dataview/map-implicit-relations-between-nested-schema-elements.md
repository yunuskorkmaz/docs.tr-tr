---
title: İç içe geçmiş şema öğeleri arasında örtük ilişkileri eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 73cd8a83021934de3b8e3bf494a4f59dd32e183c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085714"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="eaa72-102">İç içe geçmiş şema öğeleri arasında örtük ilişkileri eşleme</span><span class="sxs-lookup"><span data-stu-id="eaa72-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="eaa72-103">Bir XML Şeması Tanım Dili (XSD) şemaya karmaşık türler birbiriyle içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="eaa72-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="eaa72-104">Bu durumda, eşleme işlemi varsayılan eşleme uygular ve aşağıdakileri oluşturur <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="eaa72-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="eaa72-105">(Üst ve alt) karmaşık türlerinin her biri için bir tablo.</span><span class="sxs-lookup"><span data-stu-id="eaa72-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="eaa72-106">Üst öğede benzersiz kısıtlama yok varsa ek bir birincil anahtar sütun başına tablo tanımı adlı *TableName*_kimliği burada *TableName* üst tablo adıdır.</span><span class="sxs-lookup"><span data-stu-id="eaa72-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="eaa72-107">Ek sütun birincil anahtar olarak tanımlayan ana tablosundaki birincil anahtar kısıtlaması (ayarlayarak **IsPrimaryKey** özelliğini **True**).</span><span class="sxs-lookup"><span data-stu-id="eaa72-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="eaa72-108">Kısıtlama kısıtlaması adlı\# burada \# 1, 2, 3 ve böyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="eaa72-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="eaa72-109">Örneğin, varsayılan ilk kısıtlamayı Constraint1 adıdır.</span><span class="sxs-lookup"><span data-stu-id="eaa72-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="eaa72-110">Ek sütun üst tablonun birincil anahtarına başvurarak yabancı anahtar olarak tanımlayan alt tablo bir yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="eaa72-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="eaa72-111">Kısıtlama adlı *ParentTable_ChildTable* burada *ParentTable* üst tablo adıdır ve *geldiği* alt tablo adıdır.</span><span class="sxs-lookup"><span data-stu-id="eaa72-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="eaa72-112">Üst ve alt tablolar arasında veri ilişkisi.</span><span class="sxs-lookup"><span data-stu-id="eaa72-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="eaa72-113">Aşağıdaki örnek, bir şema gösterir. burada **OrderDetail** bir alt öğesidir **sipariş**.</span><span class="sxs-lookup"><span data-stu-id="eaa72-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="eaa72-114">Aşağıdaki XML Şeması eşleme işlemi oluşturur **veri kümesi**:</span><span class="sxs-lookup"><span data-stu-id="eaa72-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="eaa72-115">Bir **sipariş** ve **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="eaa72-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="eaa72-116">Benzersiz kısıtlama **sipariş** tablo.</span><span class="sxs-lookup"><span data-stu-id="eaa72-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="eaa72-117">Unutmayın **IsPrimaryKey** özelliği **True**.</span><span class="sxs-lookup"><span data-stu-id="eaa72-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="eaa72-118">Bir yabancı anahtar kısıtlaması **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="eaa72-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="eaa72-119">Arasında bir ilişki **sipariş** ve **OrderDetail** tablolar.</span><span class="sxs-lookup"><span data-stu-id="eaa72-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="eaa72-120">**İç içe** özelliği bu ilişki için **True** çünkü **sipariş** ve **OrderDetail** şemada öğelerini iç içe .</span><span class="sxs-lookup"><span data-stu-id="eaa72-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eaa72-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eaa72-121">See Also</span></span>  
 [<span data-ttu-id="eaa72-122">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eaa72-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="eaa72-123">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="eaa72-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="eaa72-124">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="eaa72-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
