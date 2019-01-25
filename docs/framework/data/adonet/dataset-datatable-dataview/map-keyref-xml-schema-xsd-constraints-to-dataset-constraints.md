---
title: Keyref XML Şeması (XSD) kısıtlamalarını DataSet kısıtlamaları ile eşleme
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: bc3863bbe6fd7c290c25056e2420107ed2d8bff3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732810"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Keyref XML Şeması (XSD) kısıtlamalarını DataSet kısıtlamaları ile eşleme
**Keyref** öğesi bir belge içindeki öğeleri arasında bağlantı kurmanızı sağlar. Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisi için benzer. Bir şema belirtiyorsa **keyref** öğesi, öğenin karşılık gelen bir yabancı anahtar kısıtlaması tablolar sütunlar üzerinde şema eşleme işlemi sırasında dönüştürülür <xref:System.Data.DataSet>. Varsayılan olarak, **keyref** öğesi ayrıca oluşturur bir ilişki ile **ParentTable**, **geldiği**, **ParentColumn**ve  **ChildColumn** özellikler üzerinde ilişkisi belirtilmiş.  
  
 Aşağıdaki tabloda ana hatlarını **msdata** öznitelikleri içinde belirtebileceğiniz **keyref** öğesi.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Varsa **ConstraintOnly = "true"** belirtilen **keyref** şema öğesi, bir kısıtlama oluşturuldu, ancak hiçbir ilişkisi oluşturulur. Bu öznitelik belirtilmezse (veya **False**), kısıtlama hem ilişki oluşturulan **veri kümesi**.|  
|**msdata:ConstraintName**|Varsa **ConstraintName** özniteliği belirtilirse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **adı** özniteliği **keyref** şema öğesi sağlar kısıtlama adı **veri kümesi**.|  
|**msdata:UpdateRule**|Varsa **UpdateRule** özniteliği belirtilirse **keyref** şema öğesi, değeri atanır **UpdateRule** kısıtlaması özelliğinde  **Veri kümesi**. Aksi takdirde **UpdateRule** özelliği **Cascade**.|  
|**msdata:DeleteRule**|Varsa **DeleteRule** özniteliği belirtilirse **keyref** şema öğesi, değeri atanır **DeleteRule** kısıtlaması özelliğinde  **Veri kümesi**. Aksi takdirde **DeleteRule** özelliği **Cascade**.|  
|**msdata:AcceptRejectRule**|Varsa **AcceptRejectRule** özniteliği belirtilirse **keyref** şema öğesi, değeri atanır **AcceptRejectRule** kısıtlamaözelliği **Veri kümesi**. Aksi takdirde **AcceptRejectRule** özelliği **hiçbiri**.|  
  
 Aşağıdaki örnek belirten bir şema içeriyor **anahtarı** ve **keyref** arasındaki ilişkileri **OrderNumber** alt öğesi **sırası**  öğesi ve **OrderNo** alt öğesi **OrderDetail** öğesi.  
  
 Örnekte, **OrderNumber** alt öğesi **OrderDetail** öğesi başvurduğu **OrderNo** anahtar alt öğesi **sipariş**öğesi.  
  
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
  
 Aşağıdaki XML Şeması Tanım Dili (XSD) şemaya eşleme işlemi üretir **veri kümesi** iki tabloya:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Ayrıca, **veri kümesi** aşağıdaki kısıtlamalar tanımlar:  
  
-   Benzersiz kısıtlama **sipariş** tablo.  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   Arasında bir ilişki **sipariş** ve **OrderDetail** tablolar. **İç içe** özelliği **False** iki öğe şemasında değil nedeniyle.  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   Bir yabancı anahtar kısıtlaması **OrderDetail** tablo.  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
