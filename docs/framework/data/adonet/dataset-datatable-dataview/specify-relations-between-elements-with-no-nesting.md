---
description: 'Hakkında daha fazla bilgi edinin: Iç Içe olmayan öğeler arasındaki Ilişkileri belirtme'
title: İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 68f6edad0c282091529bf9182f5161d0808a47aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651632"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="2fae7-103">İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme</span><span class="sxs-lookup"><span data-stu-id="2fae7-103">Specify Relations Between Elements with No Nesting</span></span>

<span data-ttu-id="2fae7-104">Öğeler iç içe olmadığında dolaylı ilişkiler oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="2fae7-104">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="2fae7-105">Ancak, **msdata: Relationship** ek açıklaması kullanılarak iç içe olmayan öğeler arasındaki ilişkileri açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fae7-105">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="2fae7-106">Aşağıdaki örnek, iç içe olmayan **Order** ve **OrderDetail** öğeleri arasında **msdata: ılışkı** ek açıklaması belirtilen bir XML şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fae7-106">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="2fae7-107">**Msdata: ilişki** ek açıklaması, **şema** öğesinin alt öğesi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2fae7-107">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="2fae7-108">XML şeması tanım dili (XSD) şema eşleme işlemi, bir <xref:System.Data.DataSet> **Order** ve **OrderDetail** tabloları ve aşağıda gösterildiği gibi bu iki tablo arasında belirtilen bir ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2fae7-108">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fae7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fae7-109">See also</span></span>

- [<span data-ttu-id="2fae7-110">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2fae7-110">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="2fae7-111">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="2fae7-111">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="2fae7-112">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2fae7-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
