---
title: İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 3aa9976ccde426eeda1d869164409c5235a629fe
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040046"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="61f84-102">İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme</span><span class="sxs-lookup"><span data-stu-id="61f84-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="61f84-103">Öğeler iç içe olmadığında dolaylı ilişkiler oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="61f84-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="61f84-104">Ancak, **msdata: Relationship** ek açıklaması kullanılarak iç içe olmayan öğeler arasındaki ilişkileri açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61f84-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="61f84-105">Aşağıdaki örnek, iç içe olmayan **Order** ve **OrderDetail** öğeleri arasında **msdata: ılışkı** ek açıklaması belirtilen bir XML şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61f84-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="61f84-106">**Msdata: ilişki** ek açıklaması, **şema** öğesinin alt öğesi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="61f84-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="61f84-107">XML şeması tanım dili (XSD) şema eşleme işlemi, **Order** ve **OrderDetail** tabloları ve aşağıda gösterildiği gibi bu iki tablo arasında belirtilen bir ilişki içeren bir <xref:System.Data.DataSet> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61f84-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="61f84-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61f84-108">See also</span></span>

- [<span data-ttu-id="61f84-109">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61f84-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="61f84-110">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="61f84-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="61f84-111">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="61f84-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
