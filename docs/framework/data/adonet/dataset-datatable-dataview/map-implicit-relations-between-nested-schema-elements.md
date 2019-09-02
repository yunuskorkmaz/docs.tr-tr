---
title: İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: e9ea85db98a577991e06e0239a0738a2ca5bada6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203486"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
Bir XML şeması tanım dili (XSD) şeması, bir diğeri içinde iç içe geçmiş karmaşık türlere sahip olabilir. Bu durumda, eşleme işlemi varsayılan eşlemeyi uygular ve içinde <xref:System.Data.DataSet>aşağıdakileri oluşturur:  
  
- Karmaşık türlerin her biri için bir tablo (üst ve alt).  
  
- Üst öğede benzersiz bir kısıtlama yoksa, TableName _ID adlı tablo tanımı başına bir ek birincil anahtarsütunu, *TableName* , üst tablonun adıdır.  
  
- Birincil anahtar olarak ek sütunu tanımlayan üst tabloda birincil anahtar kısıtlaması ( **IsPrimaryKey** özelliği **true**olarak ayarlanarak). Kısıtlama, 1, 2\# , \# 3 vb. olduğu kısıtlamadır. Örneğin, ilk kısıtlamanın varsayılan adı Constraint1 ' dir.  
  
- Üst tablonun birincil anahtarına başvuran yabancı anahtar olarak ek sütunu tanımlayan alt tablodaki yabancı anahtar kısıtlaması. Kısıtlama *ParentTable_ChildTable* olarak adlandırılır; burada *ParentTable* üst tablonun adı ve *ChildTable* ise alt tablonun adıdır.  
  
- Üst ve alt tablolar arasındaki bir veri ilişkisi.  
  
 Aşağıdaki örnek, **OrderDetail** 'in **sıra**alt öğesi olduğu bir şemayı gösterir.  
  
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
  
 XML Şeması eşleme işlemi, **veri kümesinde**aşağıdakileri oluşturur:  
  
- Bir **Order** ve **OrderDetail** tablosu.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- **Order** tablosundaki benzersiz bir kısıtlama. **IsPrimaryKey** özelliğinin **true**olarak ayarlandığını unutmayın.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- **OrderDetail** tablosundaki yabancı anahtar kısıtlaması.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- **Order** ve **OrderDetail** tabloları arasındaki ilişki. **Order** ve **OrderDetail** öğeleri şemada iç içe yerleştirilmiş olduğundan, bu ilişkinin **iç içe geçmiş** özelliği **true** olarak ayarlanır.  
  
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

- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
