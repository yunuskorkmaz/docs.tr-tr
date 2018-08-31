---
title: İç içe geçmiş öğeler için belirtilen ilişkileri eşleme
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 0346ba04fd8af6b5abc81fe994dd40f9a6a37c1d
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332474"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="430c7-102">İç içe geçmiş öğeler için belirtilen ilişkileri eşleme</span><span class="sxs-lookup"><span data-stu-id="430c7-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="430c7-103">Bir şema içerebilir bir **msdata:Relationship** açıkça şemada herhangi iki öğe arasındaki eşlemeyi belirtmek için ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="430c7-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="430c7-104">Belirtilen iki öğe **msdata:Relationship** şemada iç içe olabilir, ancak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="430c7-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="430c7-105">Eşleme işlemini kullanan **msdata:Relationship** iki sütun arasında birincil anahtarı/yabancı anahtar ilişkisi oluşturmak için şema.</span><span class="sxs-lookup"><span data-stu-id="430c7-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="430c7-106">Aşağıdaki örnek bir XML Şeması gösterilmektedir **OrderDetail** öğesi alt öğesi olan **sipariş**.</span><span class="sxs-lookup"><span data-stu-id="430c7-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="430c7-107">**Msdata:Relationship** bu üst-alt ilişkisi tanımlar ve belirten **OrderNumber** ortaya çıkan sütun **sipariş** tablo ilgili **OrderNo** ortaya çıkan sütun **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="430c7-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="430c7-108">Aşağıdaki XML Şeması eşleme işlemi oluşturur <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="430c7-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="430c7-109">Bir **sipariş** ve **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="430c7-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="430c7-110">Arasında bir ilişki **sipariş** ve **OrderDetail** tablolar.</span><span class="sxs-lookup"><span data-stu-id="430c7-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="430c7-111">**İç içe** özelliği bu ilişki için **True** çünkü **sipariş** ve **OrderDetail** şemada öğelerini iç içe .</span><span class="sxs-lookup"><span data-stu-id="430c7-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="430c7-112">Eşleme işlemi kısıtlamalardan oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="430c7-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430c7-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="430c7-113">See Also</span></span>  
 [<span data-ttu-id="430c7-114">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="430c7-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="430c7-115">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="430c7-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="430c7-116">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="430c7-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
