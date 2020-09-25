---
title: İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 32f8bf67242143098717b47c3b7aa175317ba274
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201323"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme

Bir XML şeması tanım dili (XSD) şeması, bir diğeri içinde iç içe geçmiş karmaşık türlere sahip olabilir. Bu durumda, eşleme işlemi varsayılan eşlemeyi uygular ve içinde aşağıdakileri oluşturur <xref:System.Data.DataSet> :  
  
- Karmaşık türlerin her biri için bir tablo (üst ve alt).  
  
- Üst öğede benzersiz bir kısıtlama yoksa, *TableName adlı tablo*tanımı başına bir ek birincil anahtar sütunu _Id, *TableName* , üst tablonun adıdır.  
  
- Birincil anahtar olarak ek sütunu tanımlayan üst tabloda birincil anahtar kısıtlaması ( **IsPrimaryKey** özelliği **true**olarak ayarlanarak). Kısıtlama, \# \# 1, 2, 3 vb. olduğu kısıtlamadır. Örneğin, ilk kısıtlamanın varsayılan adı Constraint1 ' dir.  
  
- Üst tablonun birincil anahtarına başvuran yabancı anahtar olarak ek sütunu tanımlayan alt tablodaki yabancı anahtar kısıtlaması. Kısıtlama *ParentTable_ChildTable* adlandırılır; burada *ParentTable* üst tablonun adı ve *ChildTable* ise alt tablonun adıdır.  
  
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
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- **Order** tablosundaki benzersiz bir kısıtlama. **IsPrimaryKey** özelliğinin **true**olarak ayarlandığını unutmayın.  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- **OrderDetail** tablosundaki yabancı anahtar kısıtlaması.  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- **Order** ve **OrderDetail** tabloları arasındaki ilişki. **Order** ve **OrderDetail** öğeleri şemada iç içe yerleştirilmiş olduğundan, bu ilişkinin **iç içe geçmiş** özelliği **true** olarak ayarlanır.  
  
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
