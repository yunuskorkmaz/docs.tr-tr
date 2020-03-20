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
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="fe5d2-102">İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="fe5d2-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="fe5d2-103">Şema, şemadaki herhangi iki öğe arasındaki eşlemi açıkça belirtmek için **bir msdata:İlişki** ek açıklamasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="fe5d2-104">msdata'da belirtilen iki **öğe:İlişki** şemada iç içe olabilir, ancak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="fe5d2-105">Eşleme işlemi, iki sütun arasındaki birincil anahtar/yabancı anahtar ilişkisini oluşturmak için **şemadaki msdata:İlişkiyi** kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="fe5d2-106">Aşağıdaki **örnekte, OrderDetail** öğesinin **Siparişin**alt öğesi olduğu bir XML Şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="fe5d2-107">**msdata:İlişki** bu üst-alt ilişkisini tanımlar ve elde edilen **Sipariş** tablosunun **OrderNumber** sütununun, elde edilen **OrderDetail** tablosunun **OrderNo** sütunuyla ilişkili olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="fe5d2-108">XML Şema haritalama işlemi aşağıdakileri <xref:System.Data.DataSet>oluşturur:</span><span class="sxs-lookup"><span data-stu-id="fe5d2-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="fe5d2-109">Sipariş **Order** ve **OrderDetail** tablosu.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="fe5d2-110">**Sipariş** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="fe5d2-111">Düzen ve **OrderDetail** öğeleri şemada **Order** iç içe olduğundan, bu ilişkinin İç **Içe Geçen** özelliği **True** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="fe5d2-112">Eşleme işlemi herhangi bir kısıtlama oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5d2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe5d2-113">See also</span></span>

- [<span data-ttu-id="fe5d2-114">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe5d2-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="fe5d2-115">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="fe5d2-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="fe5d2-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fe5d2-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
