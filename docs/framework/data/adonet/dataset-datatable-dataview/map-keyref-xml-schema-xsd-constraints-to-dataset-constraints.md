---
title: Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150889"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
**Keyref** öğesi, belge içindeki öğeler arasında bağlantılar kurmanızı sağlar. Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisine benzer. Şema **keyref** öğesini belirtirse, schema eşleme işlemi sırasında öğe tablolardaki sütunlarda karşılık gelen yabancı <xref:System.Data.DataSet>anahtar kısıtlamasına dönüştürülür. Varsayılan olarak, **keyref** öğesi de bir ilişki oluşturur, **ParentTable**ile, **ChildTable**, Üst Sütun , ve **ChildColumn**özellikleri ilişki üzerinde belirtilen. **ChildColumn**  
  
 Aşağıdaki tabloda **keyref** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenebilir.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|**ConstraintOnly="true"** şemadaki **keyref** öğesinde belirtilirse, bir kısıtlama oluşturulur, ancak ilişki oluşturulmaz. Bu öznitelik belirtilmemişse (veya **False**olarak ayarlanmışsa), hem kısıtlama hem de ilişki **DataSet'te**oluşturulur.|  
|**msdata:ConstraintName**|**ConstraintName** özniteliği belirtilirse, değeri kısıtlamanın adı olarak kullanılır. Aksi takdirde, şemadaki **keyref** öğesinin **ad** özniteliği **DataSet'teki**kısıtlama adını sağlar.|  
|**msdata:UpdateRule**|Şemadaki **keyref** öğesinde **UpdateRule** özniteliği belirtilirse, değeri **DataSet'teki** **UpdateRule** kısıtlama özelliğine atanır. Aksi takdirde **UpdateRule** özelliği **Basamaklı**olarak ayarlanır.|  
|**msdata:DeleteRule**|Şemadaki **keyref** öğesinde **DeleteRule** özniteliği belirtilirse, değeri **DataSet'teki** **DeleteRule** kısıtlama özelliğine atanır. Aksi takdirde **DeleteRule** özelliği **Basamaklı**olarak ayarlanır.|  
|**msdata:AcceptRejectRule**|**AcceptRejectRule** özniteliği şemadaki **keyref** öğesinde belirtilirse, değeri **DataSet'teki** **AcceptRejectRule** kısıtlama özelliğine atanır. Aksi takdirde **AcceptRejectRule** özelliği **Yok**olarak ayarlanır.|  
  
 Aşağıdaki örnek, Sipariş **öğesinin** **OrderNumber** alt öğesi ile **OrderDetail** öğesinin **OrderNo** alt öğesi arasındaki **anahtar** ve **keyref** ilişkilerini belirten bir şema içerir.  
  
 Örnekte, **OrderDetail** öğesinin **OrderNumber** alt öğesi, **Sipariş** öğesinin **OrderNo** anahtar alt öğesini ifade eder.  
  
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
  
 XML Şema tanım dili (XSD) şema eşleme işlemi iki tabloile aşağıdaki **DataSet** üretir:  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Buna ek olarak, **DataSet** aşağıdaki kısıtlamaları tanımlar:  
  
- **Sipariş** tablosunda benzersiz bir kısıtlama.  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- **Sipariş** ve **OrderDetail** tabloları arasındaki ilişki. İki öğe şemada iç içe olmadığından **İç Içe Geçen** özellik **False** olarak ayarlanır.  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- **OrderDetail** tablosunda yabancı anahtar kısıtlaması.  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
