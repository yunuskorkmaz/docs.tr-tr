---
title: İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 076e3ec6e5a00fd294fa3c6d7998cfab3a136240
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182084"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
Bir XML Şeması Tanım Dili (XSD) şemaya karmaşık türler birbiriyle içinde iç içe olabilir. Bu durumda, eşleme işlemi varsayılan eşleme uygular ve aşağıdakileri oluşturur <xref:System.Data.DataSet>:  
  
-   (Üst ve alt) karmaşık türlerinin her biri için bir tablo.  
  
-   Üst öğede benzersiz kısıtlama yok varsa ek bir birincil anahtar sütun başına tablo tanımı adlı *TableName*_kimliği burada *TableName* üst tablo adıdır.  
  
-   Ek sütun birincil anahtar olarak tanımlayan ana tablosundaki birincil anahtar kısıtlaması (ayarlayarak **IsPrimaryKey** özelliğini **True**). Kısıtlama kısıtlaması adlı\# burada \# 1, 2, 3 ve böyle devam eder. Örneğin, varsayılan ilk kısıtlamayı Constraint1 adıdır.  
  
-   Ek sütun üst tablonun birincil anahtarına başvurarak yabancı anahtar olarak tanımlayan alt tablo bir yabancı anahtar kısıtlaması. Kısıtlama adlı *ParentTable_ChildTable* burada *ParentTable* üst tablo adıdır ve *geldiği* alt tablo adıdır.  
  
-   Üst ve alt tablolar arasında veri ilişkisi.  
  
 Aşağıdaki örnek, bir şema gösterir. burada **OrderDetail** bir alt öğesidir **sipariş**.  
  
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
  
 Aşağıdaki XML Şeması eşleme işlemi oluşturur **veri kümesi**:  
  
-   Bir **sipariş** ve **OrderDetail** tablo.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Benzersiz kısıtlama **sipariş** tablo. Unutmayın **IsPrimaryKey** özelliği **True**.  
  
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
  
-   Arasında bir ilişki **sipariş** ve **OrderDetail** tablolar. **İç içe** özelliği bu ilişki için **True** çünkü **sipariş** ve **OrderDetail** şemada öğelerini iç içe .  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
