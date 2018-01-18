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
# <a name="map-implicit-relations-between-nested-schema-elements"></a>İç içe geçmiş şema öğeleri arasında örtük ilişkileri eşleme
Bir XML Şeması Tanım Dili (XSD) şeması, karmaşık türler başka içinde iç içe geçmiş olabilir. Bu durumda eşleme işlemi varsayılan eşleme uygulanır ve aşağıdakileri oluşturur <xref:System.Data.DataSet>:  
  
-   Her bir karmaşık türleri (üst ve alt) için bir tablo.  
  
-   Hiçbir kısıtlama üst öğede varsa, bir ek birincil anahtar sütununun tablo tanımının başına adlı *TableName*_ıd nerede *TableName* üst tablo adıdır.  
  
-   Ek sütun birincil anahtar olarak tanımlayan üst tablo bir birincil anahtar kısıtlaması (ayarlayarak **IsPrimaryKey** özelliğine **True**). Kısıtlama kısıtlaması adlı *#*  nerede  *#*  1, 2, 3 ve benzeri. Örneğin, varsayılan ilk kısıtlaması için Constraint1 adıdır.  
  
-   Alt tablonun ek sütun üst tablonun birincil anahtarı için başvuran yabancı anahtar olarak tanımlayan bir yabancı anahtar kısıtlaması. Kısıtlama adlı *ParentTable_ChildTable* nerede *ParentTable* üst tablo adıdır ve *geldiği* alt tablo adıdır.  
  
-   Üst ve alt tablolar arasında veri ilişki.  
  
 Aşağıdaki örnek, bir şema gösterir nerede **OrderDetail** bir alt öğesi olan **sipariş**.  
  
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
  
 Aşağıda, XML Şeması eşleme işlemi oluşturur **DataSet**:  
  
-   Bir **sipariş** ve bir **OrderDetail** tablo.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Benzersiz bir kısıtlama **sipariş** tablo. Unutmayın **IsPrimaryKey** özelliği ayarlanmış **doğru**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Bir yabancı anahtar kısıtlaması **OrderDetail** tablo.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Arasında bir ilişki **sipariş** ve **OrderDetail** tablo. **İç içe** özelliği bu ilişki için ayarlanmış **True** çünkü **sipariş** ve **OrderDetail** şemada öğeleri iç içe .  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
