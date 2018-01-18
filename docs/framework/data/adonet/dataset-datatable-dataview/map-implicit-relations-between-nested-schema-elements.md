---
title: "İç içe geçmiş şema öğeleri arasında örtük ilişkileri eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 740d45c47f46c311ed703fa11ec86a9739930944
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="d219a-102">İç içe geçmiş şema öğeleri arasında örtük ilişkileri eşleme</span><span class="sxs-lookup"><span data-stu-id="d219a-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="d219a-103">Bir XML Şeması Tanım Dili (XSD) şeması, karmaşık türler başka içinde iç içe geçmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d219a-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="d219a-104">Bu durumda eşleme işlemi varsayılan eşleme uygulanır ve aşağıdakileri oluşturur <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="d219a-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="d219a-105">Her bir karmaşık türleri (üst ve alt) için bir tablo.</span><span class="sxs-lookup"><span data-stu-id="d219a-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="d219a-106">Hiçbir kısıtlama üst öğede varsa, bir ek birincil anahtar sütununun tablo tanımının başına adlı *TableName*_ıd nerede *TableName* üst tablo adıdır.</span><span class="sxs-lookup"><span data-stu-id="d219a-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="d219a-107">Ek sütun birincil anahtar olarak tanımlayan üst tablo bir birincil anahtar kısıtlaması (ayarlayarak **IsPrimaryKey** özelliğine **True**).</span><span class="sxs-lookup"><span data-stu-id="d219a-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="d219a-108">Kısıtlama kısıtlaması adlı *#*  nerede  *#*  1, 2, 3 ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="d219a-108">The constraint is named Constraint*#* where *#* is 1, 2, 3, and so on.</span></span> <span data-ttu-id="d219a-109">Örneğin, varsayılan ilk kısıtlaması için Constraint1 adıdır.</span><span class="sxs-lookup"><span data-stu-id="d219a-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="d219a-110">Alt tablonun ek sütun üst tablonun birincil anahtarı için başvuran yabancı anahtar olarak tanımlayan bir yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="d219a-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="d219a-111">Kısıtlama adlı *ParentTable_ChildTable* nerede *ParentTable* üst tablo adıdır ve *geldiği* alt tablo adıdır.</span><span class="sxs-lookup"><span data-stu-id="d219a-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="d219a-112">Üst ve alt tablolar arasında veri ilişki.</span><span class="sxs-lookup"><span data-stu-id="d219a-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="d219a-113">Aşağıdaki örnek, bir şema gösterir nerede **OrderDetail** bir alt öğesi olan **sipariş**.</span><span class="sxs-lookup"><span data-stu-id="d219a-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="d219a-114">Aşağıda, XML Şeması eşleme işlemi oluşturur **DataSet**:</span><span class="sxs-lookup"><span data-stu-id="d219a-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="d219a-115">Bir **sipariş** ve bir **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="d219a-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="d219a-116">Benzersiz bir kısıtlama **sipariş** tablo.</span><span class="sxs-lookup"><span data-stu-id="d219a-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="d219a-117">Unutmayın **IsPrimaryKey** özelliği ayarlanmış **doğru**.</span><span class="sxs-lookup"><span data-stu-id="d219a-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="d219a-118">Bir yabancı anahtar kısıtlaması **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="d219a-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="d219a-119">Arasında bir ilişki **sipariş** ve **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="d219a-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="d219a-120">**İç içe** özelliği bu ilişki için ayarlanmış **True** çünkü **sipariş** ve **OrderDetail** şemada öğeleri iç içe .</span><span class="sxs-lookup"><span data-stu-id="d219a-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d219a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d219a-121">See Also</span></span>  
 [<span data-ttu-id="d219a-122">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d219a-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="d219a-123">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="d219a-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="d219a-124">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d219a-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
