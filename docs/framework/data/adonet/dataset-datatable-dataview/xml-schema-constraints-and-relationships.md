---
title: XML Şema Kısıtlamaları ve İlişkileri
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150720"
---
# <a name="xml-schema-constraints-and-relationships"></a>XML Şema Kısıtlamaları ve İlişkileri
XML Şema tanım dili (XSD) şemasında, kısıtlamaları (benzersiz, anahtar ve keyref kısıtlamaları) ve ilişkileri **(msdata:İlişki** ek açıklamasını kullanarak) belirtebilirsiniz. Bu konu, bir XML Şeması'nda belirtilen kısıtlamaların ve ilişkilerin <xref:System.Data.DataSet>nasıl yorumlandığını açıklar.  
  
 Genel olarak, bir XML Şeması'nda, **DataSet'te**yalnızca ilişki oluşturmak istiyorsanız **msdata:İlişki** ek açıklamasını belirtirsiniz. Daha fazla bilgi için bkz: [XML Schema'dan (XSD) Veri Seti İlişkileri Oluşturma.](generating-dataset-relations-from-xml-schema-xsd.md) **DataSet'te**kısıtlamalar oluşturmak istiyorsanız kısıtlamaları (benzersiz, anahtar ve keyref) belirtirsiniz. Anahtar ve keyref kısıtlamalarının, bu konuda daha sonra açıklandığı gibi, ilişkiler oluşturmak için de kullanıldığını unutmayın.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Anahtar ve keyref Kısıtlamalarından İlişki Oluşturma  
 **Msdata:İlişki** ek açıklamalarını belirtmek yerine, Yalnızca kısıtlamaları değil, **DataSet'teki**ilişkiyi oluşturmak için XML Şema eşleme işlemi sırasında kullanılan anahtar ve keyref kısıtlamalarını belirtebilirsiniz. Ancak, `msdata:ConstraintOnly="true"` **keyref** öğesinde belirtirseniz, **DataSet** yalnızca kısıtlamaları içerir ve ilişkiyi içermez.  
  
 Aşağıdaki örnekte, iç içe geçmemiş **Sipariş** ve **OrderDetail** öğelerini içeren bir XML Şeması gösterilmektedir. Şema da anahtar ve keyref kısıtlamaları belirtir.  
  
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
  
 XML Şema eşleme işlemi sırasında oluşturulan **DataSet,** **Sipariş** ve **OrderDetail** tablolarını içerir. Buna ek olarak, **DataSet** ilişkileri ve kısıtlamaları içerir. Aşağıdaki örnek, bu ilişkileri ve kısıtlamaları gösterir. Şema msdata belirtmez **unutmayın:İlişki** ek açıklama; bunun yerine, anahtar ve keyref kısıtlamaları ilişki oluşturmak için kullanılır.  
  
```text
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
  
 Önceki şema örneğinde, **Sipariş** ve **Sipariş Ayrıntısı** öğeleri iç içe geçmez. Aşağıdaki şema örneğinde, bu öğeler iç içe dir. Ancak, **hiçbir msdata:İlişki** ek belirtilmedi; bu nedenle, örtük bir ilişki varsayılır. Daha fazla bilgi için [bkz.](map-implicit-relations-between-nested-schema-elements.md) Şema da anahtar ve keyref kısıtlamaları belirtir.  
  
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
  
 XML Şema eşleme işleminden kaynaklanan **DataSet** iki tablo içerir:  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet** ayrıca iki ilişkiyi (biri **msdata:ilişki** ek açıklamasını, diğeri de anahtar ve keyref kısıtlamalarına dayalı) ve çeşitli kısıtlamaları içerir. Aşağıdaki örnek, ilişkileri ve kısıtlamaları gösterir.  
  
```text
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
  
 İç içe geçmiş bir tabloya atıfta bulunan bir keyref **kısıtlaması msdata:IsNested="true"** ek açıklamasını içeriyorsa, **DataSet** keyref kısıtlamasını ve ilgili benzersiz/anahtar kısıtlamasını temel alan tek bir iç içe geçmiş ilişki oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
