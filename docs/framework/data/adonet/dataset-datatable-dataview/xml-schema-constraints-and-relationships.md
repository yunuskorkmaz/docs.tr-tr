---
title: "XML şema kısıtlamaları ve ilişkileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e450954e4b0e51057e98dd329fe26c38f0ebbb05
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="23c60-102">XML şema kısıtlamaları ve ilişkileri</span><span class="sxs-lookup"><span data-stu-id="23c60-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="23c60-103">Bir XML Şeması Tanım Dili (XSD) şemasında, kısıtlamalar belirtebilirsiniz (benzersiz anahtar ve keyref kısıtlamaları) ve ilişkileri (kullanarak **msdata:Relationship** ek açıklama).</span><span class="sxs-lookup"><span data-stu-id="23c60-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="23c60-104">Bu konuda, kısıtlamalar ve bir XML şemasında belirtilen ilişkiler oluşturmak için nasıl yorumlanır açıklanmaktadır <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="23c60-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="23c60-105">Genel olarak, bir XML şeması içinde belirttiğiniz **msdata:Relationship** yalnızca ilişkileri oluşturmak istiyorsanız ek açıklama **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="23c60-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="23c60-106">Daha fazla bilgi için bkz: [oluşturma DataSet ilişkileri XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="23c60-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="23c60-107">Kısıtlamaları belirtin (benzersiz anahtar ve keyref) kısıtlamalar oluşturmak istiyorsanız **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="23c60-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="23c60-108">Anahtar ve keyref kısıtlamaları da ilişkiler oluşturmak için bu konunun ilerleyen bölümlerinde açıklandığı gibi kullanıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="23c60-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="23c60-109">Anahtar ve keyref kısıtlamaları bir ilişki oluşturma</span><span class="sxs-lookup"><span data-stu-id="23c60-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="23c60-110">Belirtme yerine **msdata:Relationship** ek açıklama, XML Şeması eşleme işlemi sırasında yalnızca kısıtlamaları aynı zamanda ilişki oluşturmakiçinkullanılananahtarvekeyrefkısıtlamalarıbelirtebilirsiniz **Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="23c60-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="23c60-111">Ancak, belirtirseniz `msdata:ConstraintOnly="true"` içinde **keyref** öğesi, **DataSet** yalnızca kısıtlamaları içerir ve ilişki dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="23c60-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="23c60-112">Aşağıdaki örnek içeren bir XML şeması gösterir **sipariş** ve **OrderDetail** değil iç içe öğeleri.</span><span class="sxs-lookup"><span data-stu-id="23c60-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="23c60-113">Şema aynı zamanda anahtar ve keyref kısıtlamaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="23c60-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="23c60-114">**DataSet** eşleme işlemini içeren XML Şeması sırasında oluşturulan **sipariş** ve **OrderDetail** tablo.</span><span class="sxs-lookup"><span data-stu-id="23c60-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="23c60-115">Ayrıca, **DataSet** ilişkileri ve kısıtlamaları içerir.</span><span class="sxs-lookup"><span data-stu-id="23c60-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="23c60-116">Aşağıdaki örnek, bu ilişkileri ve kısıtlamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="23c60-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="23c60-117">Şema belirtmediği Not **msdata:Relationship** ek açıklama; bunun yerine, anahtar ve keyref kısıtlamalar ilişkisi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23c60-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```  
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="23c60-118">Önceki örnekte şema, **sipariş** ve **OrderDetail** öğeleri içe değil.</span><span class="sxs-lookup"><span data-stu-id="23c60-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="23c60-119">Aşağıdaki şema örnekte bu öğeleri yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="23c60-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="23c60-120">Ancak, hiçbir **msdata:Relationship** ek açıklama belirtilir; bu nedenle, bir örtük ilişkisi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="23c60-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="23c60-121">Daha fazla bilgi için bkz: [harita dolaylı ilişkileri arasında iç içe geçmiş şema öğeleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="23c60-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="23c60-122">Şema aynı zamanda anahtar ve keyref kısıtlamaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="23c60-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="23c60-123">**DataSet** XML Şeması eşleme işleminden kaynaklanan iki tablo içerir:</span><span class="sxs-lookup"><span data-stu-id="23c60-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="23c60-124">**DataSet** iki ilişki de içerir (bir temel alarak **msdata:relationship** ek açıklama ve diğer temel anahtar ve keyref kısıtlamalar) ve çeşitli kısıtlamalar.</span><span class="sxs-lookup"><span data-stu-id="23c60-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="23c60-125">Aşağıdaki örnek, kısıtlamalar ve ilişkileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="23c60-125">The following example shows the relations and constraints.</span></span>  
  
```  
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="23c60-126">İç içe geçmiş bir tabloya başvuran keyref kısıtlaması içeriyorsa **msdata:IsNested = "true"** ek açıklama, **DataSet** keyref kısıtlaması bağlı tek bir iç içe geçmiş ilişki oluşturur ve ilgili benzersiz/key kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="23c60-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c60-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23c60-127">See Also</span></span>  
 [<span data-ttu-id="23c60-128">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="23c60-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="23c60-129">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="23c60-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
