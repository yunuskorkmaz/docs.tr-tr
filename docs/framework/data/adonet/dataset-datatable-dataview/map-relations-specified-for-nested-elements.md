---
title: İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: f758e1ef2c3786a102dc6bb5f6dd217b20dc5b55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198554"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="b98a8-102">İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="b98a8-102">Map Relations Specified for Nested Elements</span></span>

<span data-ttu-id="b98a8-103">Şemada, şemadaki iki öğe arasındaki eşlemeyi açıkça belirtmek için bir **msdata: ilişki** ek açıklaması bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b98a8-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="b98a8-104">**Msdata: Relationship** içinde belirtilen iki öğe şemada iç içe bulunabilir, ancak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b98a8-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="b98a8-105">Eşleme işlemi, iki sütun arasında birincil anahtar/yabancı anahtar ilişkisi oluşturmak için şemadaki **msdata: Relationship** kullanır.</span><span class="sxs-lookup"><span data-stu-id="b98a8-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="b98a8-106">Aşağıdaki örnek, **OrderDetail** öğesinin **Order**öğesinin bir alt öğesi olduğu bir XML şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b98a8-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="b98a8-107">**Msdata: Relationship** bu üst-alt ilişkiyi tanımlar ve sonuçta elde edilen **sipariş** tablosunun **OrderNumber** sütununun, sonuçta elde edilen **OrderDetail** tablosunun **OrderNo** sütunuyla ilişkili olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b98a8-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="b98a8-108">XML Şeması eşleme işlemi içinde aşağıdakileri oluşturur <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="b98a8-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="b98a8-109">Bir **Order** ve **OrderDetail** tablosu.</span><span class="sxs-lookup"><span data-stu-id="b98a8-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="b98a8-110">**Order** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="b98a8-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="b98a8-111">**Order** ve **OrderDetail** öğeleri şemada iç içe yerleştirilmiş olduğundan, bu ilişkinin **iç içe geçmiş** özelliği **true** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b98a8-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="b98a8-112">Eşleme işlemi herhangi bir kısıtlama oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="b98a8-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98a8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b98a8-113">See also</span></span>

- [<span data-ttu-id="b98a8-114">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b98a8-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="b98a8-115">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="b98a8-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="b98a8-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b98a8-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
