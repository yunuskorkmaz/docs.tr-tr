---
title: "Harita keyref DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e364efe0856a5291fc8157ef6ab185c2438a3347
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Harita keyref DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları
**Keyref** öğesi bir belgedeki öğeler arasında bağlantı kurmanızı sağlar. Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisi için benzer. Bir şema belirtiyorsa **keyref** öğesi, öğenin karşılık gelen bir yabancı anahtar kısıtlaması tablolardaki sütunlarda şema eşleme işlemi sırasında dönüştürülür <xref:System.Data.DataSet>. Varsayılan olarak, **keyref** öğesi de oluşturur bir ilişki ile **ParentTable**, **geldiği**, **ParentColumn**ve  **ChildColumn** özellikler üzerinde ilişkisi belirtilmiş.  
  
 Aşağıdaki tabloda ana hatlarını **msdata** içinde belirtebilirsiniz öznitelikleri **keyref** öğesi.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Varsa **ConstraintOnly = "true"** belirtilen **keyref** schema öğesinde, bir kısıtlama oluşturuldu, ancak hiçbir ilişkisi oluşturulur. Bu öznitelik belirtilmediğinde (veya ayarlamak **False**), kısıtlamayı ve ilişki oluşturulan **DataSet**.|  
|**msdata:ConstraintName**|Varsa **ConstraintName** özniteliği belirtilmezse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **adı** özniteliği **keyref** schema öğesinde sağlar ve kısıtlama adını **DataSet**.|  
|**msdata:UpdateRule**|Varsa **UpdateRule** özniteliği belirtilen **keyref** schema öğesinde değerini atanması **UpdateRule** kısıtlaması özelliğinde  **Veri kümesi**. Aksi takdirde **UpdateRule** özelliği ayarlanmış **Cascade**.|  
|**msdata:DeleteRule**|Varsa **DeleteRule** özniteliği belirtilen **keyref** schema öğesinde değerini atanması **DeleteRule** kısıtlaması özelliğinde  **Veri kümesi**. Aksi takdirde **DeleteRule** özelliği ayarlanmış **Cascade**.|  
|**msdata:AcceptRejectRule**|Varsa **AcceptRejectRule** özniteliği belirtilen **keyref** schema öğesinde değerini atanması **AcceptRejectRule** kısıtlamasıözelliği **Veri kümesi**. Aksi takdirde **AcceptRejectRule** özelliği ayarlanmış **hiçbiri**.|  
  
 Aşağıdaki örnek belirten bir şema içeriyor **anahtar** ve **keyref** arasındaki ilişkileri **OrderNumber** alt öğesi olan **sırası**  öğesi ve **OrderNo** alt öğesi olan **OrderDetail** öğesi.  
  
 Örnekte, **OrderNumber** alt öğesi olan **OrderDetail** öğesi başvurduğu **OrderNo** anahtar alt öğesi olan **sipariş**öğesi.  
  
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
  
 Aşağıdaki XML Şeması Tanım Dili (XSD) şema eşleme işlemi üreten **DataSet** iki tablo ile:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Ayrıca, **DataSet** aşağıdaki kısıtlamalar tanımlar:  
  
-   Benzersiz bir kısıtlama **sipariş** tablo.  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   Arasında bir ilişki **sipariş** ve **OrderDetail** tablo. **İç içe** özelliği ayarlanmış **False** iki öğe şemada iç içe değil çünkü.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
