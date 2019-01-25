---
title: İç içe yerleştirme içermeyen öğeler arasındaki ilişkileri belirtme
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: e33a445d4ef969c73ab9756c5aa5116fae67ea66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739186"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="0d197-102">İç içe yerleştirme içermeyen öğeler arasındaki ilişkileri belirtme</span><span class="sxs-lookup"><span data-stu-id="0d197-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="0d197-103">Öğeleri iç içe değil, hiçbir örtük ilişkileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0d197-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="0d197-104">Bununla birlikte, aşağıdakileri yapabilirsiniz açıkça belirtmeniz kullanarak iç içe olmayan öğeler arasındaki ilişkileri **msdata:Relationship** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="0d197-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="0d197-105">Aşağıdaki örnek bir XML Şeması gösterilmektedir **msdata:Relationship** arasında ek açıklaması belirtildiğinde **sipariş** ve **OrderDetail** olmayan öğeler iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="0d197-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="0d197-106">**Msdata:Relationship** ek açıklama alt öğesi olarak belirtilen **şema** öğesi.</span><span class="sxs-lookup"><span data-stu-id="0d197-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="0d197-107">XML Şeması Tanım Dili (XSD) şemaya eşleme işlemi oluşturur bir <xref:System.Data.DataSet> ile **sipariş** ve **OrderDetail** tabloları ve aşağıda gösterildiği gibi bu iki tablo arasında belirtilen bir ilişki.</span><span class="sxs-lookup"><span data-stu-id="0d197-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d197-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d197-108">See also</span></span>
- [<span data-ttu-id="0d197-109">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d197-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="0d197-110">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="0d197-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="0d197-111">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0d197-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
