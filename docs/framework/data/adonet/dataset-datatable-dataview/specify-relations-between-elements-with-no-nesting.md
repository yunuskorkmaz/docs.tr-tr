---
title: İç içe yerleştirme içermeyen öğeler arasındaki ilişkileri belirtme
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: d04a3d946b87c7203497313c6e21a75ef69f50eb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080114"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a>İç içe yerleştirme içermeyen öğeler arasındaki ilişkileri belirtme
Öğeleri iç içe değil, hiçbir örtük ilişkileri oluşturulur. Bununla birlikte, aşağıdakileri yapabilirsiniz açıkça belirtmeniz kullanarak iç içe olmayan öğeler arasındaki ilişkileri **msdata:Relationship** ek açıklama.  
  
 Aşağıdaki örnek bir XML Şeması gösterilmektedir **msdata:Relationship** arasında ek açıklaması belirtildiğinde **sipariş** ve **OrderDetail** olmayan öğeler iç içe geçmiş. **Msdata:Relationship** ek açıklama alt öğesi olarak belirtilen **şema** öğesi.  
  
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
  
 XML Şeması Tanım Dili (XSD) şemaya eşleme işlemi oluşturur bir <xref:System.Data.DataSet> ile **sipariş** ve **OrderDetail** tabloları ve aşağıda gösterildiği gibi bu iki tablo arasında belirtilen bir ilişki.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
