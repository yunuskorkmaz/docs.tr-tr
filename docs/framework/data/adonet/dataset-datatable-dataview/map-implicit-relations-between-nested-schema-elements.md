---
title: İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150969"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
Bir XML Şema tanım dili (XSD) şeması, birbirinin içinde iç içe olan karmaşık türlere sahip olabilir. Bu durumda, eşleme işlemi varsayılan eşleme uygular ve <xref:System.Data.DataSet>aşağıdaki leri oluşturur:  
  
- Karmaşık türlerin her biri (üst ve alt) için bir tablo.  
  
- Üst öğede benzersiz bir kısıtlama yoksa, *Tablo Adı*adı verilen tablo başına bir ek birincil anahtar sütunu, Tablo *Adı'nın* ana tablonun adı olduğu _Id.  
  
- Ek sütunu birincil anahtar olarak tanımlayan üst tablodaki birincil anahtar kısıtlaması **(IsPrimaryKey** özelliğini **True**olarak ayarlayarak). Kısıtlama, 1,\# \# 2, 3 ve benzeri yerlerde Kısıtlama olarak adlandırılır. Örneğin, ilk kısıtlama için varsayılan adı Kısıtlama1 olduğunu.  
  
- Alt tablodaki yabancı anahtar kısıtlaması, ek sütunu ana tablonun birincil anahtarına başvuran yabancı anahtar olarak tanımlar. Kısıtlama, *ParentTable'ın* üst tablonun adı, *ChildTable'ın* alt tablonun adı olduğu ParentTable_ChildTable adlandırılır. *ParentTable*  
  
- Üst ve alt tablolar arasında bir veri ilişkisi.  
  
 Aşağıdaki **örnekte, OrderDetail'ın** **Sipariş'in**alt öğesi olduğu bir şema gösterilmektedir.  
  
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
  
 XML Şema eşleme işlemi **DataSet'te**aşağıdakileri oluşturur:  
  
- Sipariş **Order** ve **OrderDetail** tablosu.  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- **Sipariş** tablosunda benzersiz bir kısıtlama. **IsPrimaryKey** özelliğinin **True**olarak ayarladığını unutmayın.  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- **OrderDetail** tablosunda yabancı anahtar kısıtlaması.  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- **Sipariş** ve **OrderDetail** tabloları arasındaki ilişki. Düzen ve **OrderDetail** öğeleri şemada **Order** iç içe olduğundan, bu ilişkinin İç **Içe Geçen** özelliği **True** olarak ayarlanır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
