---
title: İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: bee427c6cdf76792773ea827c8772b276ff29c31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150824"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a>İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme
Öğeler iç içe geçmediğinde, örtük ilişki oluşturulmaz. Ancak, **msdata:İlişki** ek açıklamasını kullanarak iç içe geçmemiş öğeler arasındaki ilişkileri açıkça belirtebilirsiniz.  
  
 Aşağıdaki örnekte, **msdata:İlişki** ek açıklamanın İç içe geçmemiş **Sipariş** ve **OrderDetail** öğeleri arasında belirtildiği bir XML Şeması gösterilmektedir. **msdata:İlişki** ek gösterimi **Şema** öğesinin alt öğesi olarak belirtilir.  
  
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
  
 XML Şema tanım dili (XSD) şema eşleme <xref:System.Data.DataSet> işlemi, Aşağıda gösterildiği **gibi, Sipariş** ve **OrderDetail** tabloları ve bu iki tablo arasında belirtilen bir ilişki oluşturur.  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
