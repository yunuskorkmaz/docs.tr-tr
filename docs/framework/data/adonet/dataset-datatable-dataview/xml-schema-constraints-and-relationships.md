---
title: XML Şema Kısıtlamaları ve İlişkileri
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 1ffb11814be14b3f9601abaad6e95c00f9f7a634
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202983"
---
# <a name="xml-schema-constraints-and-relationships"></a>XML Şema Kısıtlamaları ve İlişkileri
Bir XML şeması tanım dili (XSD) şemasında, kısıtlamalar (benzersiz, anahtar ve keyref kısıtlamaları) ve ilişkileri ( **msdata: Relationship** ek açıklaması kullanılarak) belirtebilirsiniz. Bu konuda bir XML şemasında belirtilen kısıtlamaların ve ilişkilerin, <xref:System.Data.DataSet>oluşturmak için nasıl yorumlanacağı açıklanmaktadır.  
  
 Genel olarak, bir XML şemasında, **veri kümesinde**yalnızca ilişkiler oluşturmak istiyorsanız **msdata: Relationship** ek açıklamasını belirtirsiniz. Daha fazla bilgi için bkz. [xml şemasından (xsd) veri kümesi Ilişkileri oluşturma](generating-dataset-relations-from-xml-schema-xsd.md). **Veri kümesinde**kısıtlamalar oluşturmak istiyorsanız kısıtlamalar (Unique, Key ve keyref) belirtirsiniz. Anahtar ve keyref kısıtlamalarının, bu konunun ilerleyen kısımlarında açıklandığı gibi ilişkiler oluşturmak için de kullanıldığını unutmayın.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Anahtar ve keyref kısıtlamalarından bir Ilişki oluşturma  
 **Msdata: ilişki** ek açıklamasını belirtmek yerıne, XML Şeması eşleme işlemi sırasında yalnızca kısıtlamaları değil, **veri kümesindeki**ilişkiyi değil, anahtar ve keyref kısıtlamalarını belirtebilirsiniz. Ancak, **keyref** öğesinde belirtirseniz `msdata:ConstraintOnly="true"` , **veri kümesi** yalnızca kısıtlamaları içerir ve ilişkiyi içermez.  
  
 Aşağıdaki örnek, iç içe olmayan **Order** ve **OrderDetail** öğelerini içeren bir XML şemasını gösterir. Şema ayrıca Key ve keyref kısıtlamalarını da belirtir.  
  
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
  
 XML Şeması eşleme işlemi sırasında oluşturulan **veri kümesi** **Order** ve **OrderDetail** tablolarını içerir. Ayrıca, **veri kümesi** ilişkiler ve kısıtlamalar içerir. Aşağıdaki örnek bu ilişkileri ve kısıtlamaları gösterir. Şemanın **msdata: ilişki** ek açıklamasını belirtmediğini unutmayın. Bunun yerine, anahtar ve keyref kısıtlamaları ilişkiyi oluşturmak için kullanılır.  
  
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
  
 Önceki şema örneğinde **Order** ve **OrderDetail** öğeleri iç içe değildir. Aşağıdaki şema örneğinde, bu öğeler iç içe. Ancak, **msdata yok: ilişki** ek açıklaması belirtilmedi; Bu nedenle, örtük bir ilişki varsayılır. Daha fazla bilgi için bkz. [Iç Içe geçmiş şema öğeleri arasında örtük Ilişkileri eşleme](map-implicit-relations-between-nested-schema-elements.md). Şema ayrıca Key ve keyref kısıtlamalarını da belirtir.  
  
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
  
 XML Şeması eşleme işleminden kaynaklanan **veri kümesi** iki tablo içerir:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **Veri kümesi** aynı zamanda iki ilişkiyi de içerir (bir diğeri **msdata: ilişki** ek açıklamasına ve diğeri anahtar ve keyref kısıtlamalarına bağlı olarak) ve çeşitli kısıtlamalara sahiptir. Aşağıdaki örnekte ilişkiler ve kısıtlamalar gösterilmektedir.  
  
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
  
 İç içe geçmiş bir tabloya başvuran bir keyref kısıtlaması **msdata: IsNested = "true"** ek açıklamasını Içeriyorsa, **veri kümesi** , keyref kısıtlamasına ve ilgili benzersiz/anahtar kısıtlamasına dayalı tek bir iç içe ilişki oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
