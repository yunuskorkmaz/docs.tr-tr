---
title: İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 83dce7173c016a7d7d2d626bb7a3606de29d54ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204471"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a>İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme
Öğeler iç içe olmadığında dolaylı ilişkiler oluşturulmaz. Ancak, **msdata: Relationship** ek açıklaması kullanılarak iç içe olmayan öğeler arasındaki ilişkileri açıkça belirtebilirsiniz.  
  
 Aşağıdaki örnek, iç içe olmayan **Order** ve **OrderDetail** öğeleri arasında **msdata: ılışkı** ek açıklaması belirtilen bir XML şemasını gösterir. **Msdata: ilişki** ek açıklaması, **şema** öğesinin alt öğesi olarak belirtilir.  
  
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
  
 XML şeması tanım dili (xsd) şema eşleme işlemi, bir <xref:System.Data.DataSet> **Order** ve **OrderDetail** tabloları ve aşağıda gösterildiği gibi bu iki tablo arasında belirtilen bir ilişki oluşturur.  
  
```  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
