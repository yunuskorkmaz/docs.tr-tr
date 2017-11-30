---
title: "XML şema kısıtlamaları ve ilişkileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a324c3b7f24d3395382067ea5581313af58e13f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-constraints-and-relationships"></a>XML şema kısıtlamaları ve ilişkileri
Bir XML Şeması Tanım Dili (XSD) şemasında, kısıtlamalar belirtebilirsiniz (benzersiz anahtar ve keyref kısıtlamaları) ve ilişkileri (kullanarak **msdata:Relationship** ek açıklama). Bu konuda, kısıtlamalar ve bir XML şemasında belirtilen ilişkiler oluşturmak için nasıl yorumlanır açıklanmaktadır <xref:System.Data.DataSet>.  
  
 Genel olarak, bir XML şeması içinde belirttiğiniz **msdata:Relationship** yalnızca ilişkileri oluşturmak istiyorsanız ek açıklama **DataSet**. Daha fazla bilgi için bkz: [oluşturma DataSet ilişkileri XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md). Kısıtlamaları belirtin (benzersiz anahtar ve keyref) kısıtlamalar oluşturmak istiyorsanız **DataSet**. Anahtar ve keyref kısıtlamaları da ilişkiler oluşturmak için bu konunun ilerleyen bölümlerinde açıklandığı gibi kullanıldığını unutmayın.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Anahtar ve keyref kısıtlamaları bir ilişki oluşturma  
 Belirtme yerine **msdata:Relationship** ek açıklama, XML Şeması eşleme işlemi sırasında yalnızca kısıtlamaları aynı zamanda ilişki oluşturmakiçinkullanılananahtarvekeyrefkısıtlamalarıbelirtebilirsiniz **Veri kümesi**. Ancak, belirtirseniz `msdata:ConstraintOnly="true"` içinde **keyref** öğesi, **DataSet** yalnızca kısıtlamaları içerir ve ilişki dahil edilmez.  
  
 Aşağıdaki örnek içeren bir XML şeması gösterir **sipariş** ve **OrderDetail** değil iç içe öğeleri. Şema aynı zamanda anahtar ve keyref kısıtlamaları belirtir.  
  
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
  
 **DataSet** eşleme işlemini içeren XML Şeması sırasında oluşturulan **sipariş** ve **OrderDetail** tablo. Ayrıca, **DataSet** ilişkileri ve kısıtlamaları içerir. Aşağıdaki örnek, bu ilişkileri ve kısıtlamaları gösterir. Şema belirtmediği Not **msdata:Relationship** ek açıklama; bunun yerine, anahtar ve keyref kısıtlamalar ilişkisi oluşturmak için kullanılır.  
  
```  
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 Önceki örnekte şema, **sipariş** ve **OrderDetail** öğeleri içe değil. Aşağıdaki şema örnekte bu öğeleri yerleştirilir. Ancak, hiçbir **msdata:Relationship** ek açıklama belirtilir; bu nedenle, bir örtük ilişkisi varsayılır. Daha fazla bilgi için bkz: [harita dolaylı ilişkileri arasında iç içe geçmiş şema öğeleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md). Şema aynı zamanda anahtar ve keyref kısıtlamaları belirtir.  
  
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
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
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
  
 **DataSet** XML Şeması eşleme işleminden kaynaklanan iki tablo içerir:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet** iki ilişki de içerir (bir temel alarak **msdata:relationship** ek açıklama ve diğer temel anahtar ve keyref kısıtlamalar) ve çeşitli kısıtlamalar. Aşağıdaki örnek, kısıtlamalar ve ilişkileri gösterir.  
  
```  
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 İç içe geçmiş bir tabloya başvuran keyref kısıtlaması içeriyorsa **msdata:IsNested = "true"** ek açıklama, **DataSet** keyref kısıtlaması bağlı tek bir iç içe geçmiş ilişki oluşturur ve ilgili benzersiz/key kısıtlaması.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türetilen DataSet ilişkisel yapısından XML Şeması (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
