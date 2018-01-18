---
title: "Hiçbir iç içe geçme ile öğeleri arasındaki ilişkileri belirtin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cf17031dd6e562d365ff94ab94b3b99a0dd6f747
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="1b7e4-102">Hiçbir iç içe geçme ile öğeleri arasındaki ilişkileri belirtin</span><span class="sxs-lookup"><span data-stu-id="1b7e4-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="1b7e4-103">Öğeleri içe değil, hiçbir dolaylı ilişkileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1b7e4-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="1b7e4-104">Ancak, şunları yapabilirsiniz açıkça belirtmek kullanarak iç içe değil öğeleri arasındaki ilişkileri **msdata:Relationship** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="1b7e4-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="1b7e4-105">Aşağıdaki örnek bir XML şeması gösterir **msdata:Relationship** arasında ek açıklama belirtilen **sipariş** ve **OrderDetail** olmayan öğeler iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="1b7e4-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="1b7e4-106">**Msdata:Relationship** ek açıklama alt öğesi olarak belirtilen **şema** öğesi.</span><span class="sxs-lookup"><span data-stu-id="1b7e4-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="1b7e4-107">XML Şeması Tanım Dili (XSD) şema eşleme işlemi oluşturur bir <xref:System.Data.DataSet> ile **sipariş** ve **OrderDetail** tablolar ve aşağıda gösterildiği gibi bu iki tablo arasında belirtilen bir ilişki.</span><span class="sxs-lookup"><span data-stu-id="1b7e4-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b7e4-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b7e4-108">See Also</span></span>  
 [<span data-ttu-id="1b7e4-109">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b7e4-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="1b7e4-110">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="1b7e4-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="1b7e4-111">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1b7e4-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
