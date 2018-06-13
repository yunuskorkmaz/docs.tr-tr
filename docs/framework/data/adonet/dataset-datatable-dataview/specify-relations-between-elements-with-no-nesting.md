---
title: Hiçbir iç içe geçme ile öğeleri arasındaki ilişkileri belirtin
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 1d178287150dfca4c379cf6e934370434c3cfc98
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760095"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a>Hiçbir iç içe geçme ile öğeleri arasındaki ilişkileri belirtin
Öğeleri içe değil, hiçbir dolaylı ilişkileri oluşturulur. Ancak, şunları yapabilirsiniz açıkça belirtmek kullanarak iç içe değil öğeleri arasındaki ilişkileri **msdata:Relationship** ek açıklama.  
  
 Aşağıdaki örnek bir XML şeması gösterir **msdata:Relationship** arasında ek açıklama belirtilen **sipariş** ve **OrderDetail** olmayan öğeler iç içe geçmiş. **Msdata:Relationship** ek açıklama alt öğesi olarak belirtilen **şema** öğesi.  
  
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
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"   
                            msdata:child="OrderDetail"   
                            msdata:parentkey="OrderNumber"   
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 XML Şeması Tanım Dili (XSD) şema eşleme işlemi oluşturur bir <xref:System.Data.DataSet> ile **sipariş** ve **OrderDetail** tablolar ve aşağıda gösterildiği gibi bu iki tablo arasında belirtilen bir ilişki.  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
