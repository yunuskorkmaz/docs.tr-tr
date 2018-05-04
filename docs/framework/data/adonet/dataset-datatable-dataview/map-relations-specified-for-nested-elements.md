---
title: İç içe geçmiş öğe için belirtilen ilişkileri eşleme
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: e1fde0ef585621a6821838613a7e77dedf7042b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="map-relations-specified-for-nested-elements"></a>İç içe geçmiş öğe için belirtilen ilişkileri eşleme
Bir şema dahil edebileceğiniz bir **msdata:Relationship** herhangi iki şema öğeleri arasında eşleme açıkça belirtmek için ek açıklama. Belirtilen iki öğe **msdata:Relationship** şemada iç içe olabilir, ancak olması gerekmez. Eşleme işlemini kullanan **msdata:Relationship** iki sütun arasında birincil anahtarı/yabancı anahtar ilişkisi oluşturmak için şemada.  
  
 Aşağıdaki örnek bir XML şeması gösterir **OrderDetail** öğesi bir alt öğedir **sipariş**. **Msdata:Relationship** bu üst-alt ilişkisi tanımlar ve belirten **OrderNumber** elde edilen, sütun **sipariş** tablo ile ilgili **OrderNo** elde edilen, sütun **OrderDetail** tablo.  
  
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
  
 Aşağıda, XML Şeması eşleme işlemi oluşturur <xref:System.Data.DataSet>:  
  
-   Bir **sipariş** ve bir **OrderDetail** tablo.  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   Arasında bir ilişki **sipariş** ve **OrderDetail** tablo. **İç içe** özelliği bu ilişki için ayarlanmış **True** çünkü **sipariş** ve **OrderDetail** şemada öğeleri iç içe .  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Eşleme işlemini kısıtlamalar oluşturmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
