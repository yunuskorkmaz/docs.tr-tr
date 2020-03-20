---
title: XML Şema Kısıtlamaları ve İlişkileri
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150720"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="69b34-102">XML Şema Kısıtlamaları ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="69b34-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="69b34-103">XML Şema tanım dili (XSD) şemasında, kısıtlamaları (benzersiz, anahtar ve keyref kısıtlamaları) ve ilişkileri **(msdata:İlişki** ek açıklamasını kullanarak) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b34-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="69b34-104">Bu konu, bir XML Şeması'nda belirtilen kısıtlamaların ve ilişkilerin <xref:System.Data.DataSet>nasıl yorumlandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="69b34-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="69b34-105">Genel olarak, bir XML Şeması'nda, **DataSet'te**yalnızca ilişki oluşturmak istiyorsanız **msdata:İlişki** ek açıklamasını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b34-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="69b34-106">Daha fazla bilgi için bkz: [XML Schema'dan (XSD) Veri Seti İlişkileri Oluşturma.](generating-dataset-relations-from-xml-schema-xsd.md)</span><span class="sxs-lookup"><span data-stu-id="69b34-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="69b34-107">**DataSet'te**kısıtlamalar oluşturmak istiyorsanız kısıtlamaları (benzersiz, anahtar ve keyref) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b34-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="69b34-108">Anahtar ve keyref kısıtlamalarının, bu konuda daha sonra açıklandığı gibi, ilişkiler oluşturmak için de kullanıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="69b34-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="69b34-109">Anahtar ve keyref Kısıtlamalarından İlişki Oluşturma</span><span class="sxs-lookup"><span data-stu-id="69b34-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="69b34-110">**Msdata:İlişki** ek açıklamalarını belirtmek yerine, Yalnızca kısıtlamaları değil, **DataSet'teki**ilişkiyi oluşturmak için XML Şema eşleme işlemi sırasında kullanılan anahtar ve keyref kısıtlamalarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b34-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="69b34-111">Ancak, `msdata:ConstraintOnly="true"` **keyref** öğesinde belirtirseniz, **DataSet** yalnızca kısıtlamaları içerir ve ilişkiyi içermez.</span><span class="sxs-lookup"><span data-stu-id="69b34-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="69b34-112">Aşağıdaki örnekte, iç içe geçmemiş **Sipariş** ve **OrderDetail** öğelerini içeren bir XML Şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="69b34-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="69b34-113">Şema da anahtar ve keyref kısıtlamaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="69b34-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="69b34-114">XML Şema eşleme işlemi sırasında oluşturulan **DataSet,** **Sipariş** ve **OrderDetail** tablolarını içerir.</span><span class="sxs-lookup"><span data-stu-id="69b34-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="69b34-115">Buna ek olarak, **DataSet** ilişkileri ve kısıtlamaları içerir.</span><span class="sxs-lookup"><span data-stu-id="69b34-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="69b34-116">Aşağıdaki örnek, bu ilişkileri ve kısıtlamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="69b34-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="69b34-117">Şema msdata belirtmez **unutmayın:İlişki** ek açıklama; bunun yerine, anahtar ve keyref kısıtlamaları ilişki oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69b34-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```text
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
  
 <span data-ttu-id="69b34-118">Önceki şema örneğinde, **Sipariş** ve **Sipariş Ayrıntısı** öğeleri iç içe geçmez.</span><span class="sxs-lookup"><span data-stu-id="69b34-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="69b34-119">Aşağıdaki şema örneğinde, bu öğeler iç içe dir.</span><span class="sxs-lookup"><span data-stu-id="69b34-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="69b34-120">Ancak, **hiçbir msdata:İlişki** ek belirtilmedi; bu nedenle, örtük bir ilişki varsayılır.</span><span class="sxs-lookup"><span data-stu-id="69b34-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="69b34-121">Daha fazla bilgi için [bkz.](map-implicit-relations-between-nested-schema-elements.md)</span><span class="sxs-lookup"><span data-stu-id="69b34-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="69b34-122">Şema da anahtar ve keyref kısıtlamaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="69b34-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="69b34-123">XML Şema eşleme işleminden kaynaklanan **DataSet** iki tablo içerir:</span><span class="sxs-lookup"><span data-stu-id="69b34-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="69b34-124">**DataSet** ayrıca iki ilişkiyi (biri **msdata:ilişki** ek açıklamasını, diğeri de anahtar ve keyref kısıtlamalarına dayalı) ve çeşitli kısıtlamaları içerir.</span><span class="sxs-lookup"><span data-stu-id="69b34-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="69b34-125">Aşağıdaki örnek, ilişkileri ve kısıtlamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="69b34-125">The following example shows the relations and constraints.</span></span>  
  
```text
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
  
 <span data-ttu-id="69b34-126">İç içe geçmiş bir tabloya atıfta bulunan bir keyref **kısıtlaması msdata:IsNested="true"** ek açıklamasını içeriyorsa, **DataSet** keyref kısıtlamasını ve ilgili benzersiz/anahtar kısıtlamasını temel alan tek bir iç içe geçmiş ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69b34-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b34-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69b34-127">See also</span></span>

- [<span data-ttu-id="69b34-128">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="69b34-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="69b34-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="69b34-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
