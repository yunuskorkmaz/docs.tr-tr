---
title: İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150902"
---
# <a name="map-relations-specified-for-nested-elements"></a>İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme
Şema, şemadaki herhangi iki öğe arasındaki eşlemi açıkça belirtmek için **bir msdata:İlişki** ek açıklamasını içerebilir. msdata'da belirtilen iki **öğe:İlişki** şemada iç içe olabilir, ancak olması gerekmez. Eşleme işlemi, iki sütun arasındaki birincil anahtar/yabancı anahtar ilişkisini oluşturmak için **şemadaki msdata:İlişkiyi** kullanır.  
  
 Aşağıdaki **örnekte, OrderDetail** öğesinin **Siparişin**alt öğesi olduğu bir XML Şeması gösterilmektedir. **msdata:İlişki** bu üst-alt ilişkisini tanımlar ve elde edilen **Sipariş** tablosunun **OrderNumber** sütununun, elde edilen **OrderDetail** tablosunun **OrderNo** sütunuyla ilişkili olduğunu belirtir.  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 XML Şema haritalama işlemi aşağıdakileri <xref:System.Data.DataSet>oluşturur:  
  
- Sipariş **Order** ve **OrderDetail** tablosu.  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- **Sipariş** ve **OrderDetail** tabloları arasındaki ilişki. Düzen ve **OrderDetail** öğeleri şemada **Order** iç içe olduğundan, bu ilişkinin İç **Içe Geçen** özelliği **True** olarak ayarlanır.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Eşleme işlemi herhangi bir kısıtlama oluşturmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
