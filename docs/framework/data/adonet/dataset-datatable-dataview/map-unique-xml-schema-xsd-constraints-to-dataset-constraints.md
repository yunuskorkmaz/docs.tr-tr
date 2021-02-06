---
description: 'Hakkında daha fazla bilgi edinin: benzersiz XML şeması (XSD) kısıtlamalarını veri kümesi kısıtlamalarına eşleme'
title: Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 41a6e5424d67b092e57ac61d6e34a1f285fb8d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651931"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="f217b-103">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="f217b-103">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="f217b-104">Bir XML şeması tanım dili (XSD) şemasında, **Unique** öğesi bir öğe veya öznitelik üzerinde benzersizlik kısıtlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f217b-104">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="f217b-105">Bir XML şemasını ilişkisel bir şemaya çevirme işleminde, XML şemasında bir öğe veya öznitelik üzerinde belirtilen benzersiz kısıtlama, karşılık gelen ' de bulunan içinde benzersiz bir kısıtlamaya eşlenir <xref:System.Data.DataTable> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="f217b-105">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="f217b-106">Aşağıdaki tabloda, **benzersiz** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f217b-106">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="f217b-107">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="f217b-107">Attribute name</span></span>|<span data-ttu-id="f217b-108">Description</span><span class="sxs-lookup"><span data-stu-id="f217b-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f217b-109">**msdata: ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="f217b-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="f217b-110">Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f217b-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="f217b-111">Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f217b-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="f217b-112">**msdata: PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="f217b-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="f217b-113">`PrimaryKey="true"` **Unique** öğesinde varsa, **IsPrimaryKey** özelliği **true** olarak ayarlanan bir Unique kısıtlaması oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f217b-113">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="f217b-114">Aşağıdaki örnek, bir benzersizlik kısıtlaması belirtmek için **benzersiz** öğe kullanan bir XML şeması gösterir.</span><span class="sxs-lookup"><span data-stu-id="f217b-114">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="f217b-115">Şemadaki **benzersiz** öğe, bir belge örneğindeki tüm **müşteriler** öğeleri için, **MüşteriNo** alt öğesinin değerinin benzersiz olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f217b-115">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="f217b-116">**Veri kümesini** oluştururken, eşleme işlemi bu şemayı okur ve aşağıdaki tabloyu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f217b-116">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="f217b-117">Eşleme işlemi, aşağıdaki **veri kümesinde** gösterildiği gibi **MüşteriNo** sütununda de benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f217b-117">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="f217b-118">(Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)</span><span class="sxs-lookup"><span data-stu-id="f217b-118">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="f217b-119">Oluşturulan **veri kümesinde** , **IsPrimaryKey** özelliği, Unique kısıtlaması için **false** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f217b-119">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="f217b-120">Sütunundaki **UNIQUE** özelliği, **MüşteriNo** sütun değerlerinin benzersiz olması gerektiğini belirtir (ancak sütunun **AllowDBNull** özelliği tarafından belirtilen şekilde null bir başvuru olabilir).</span><span class="sxs-lookup"><span data-stu-id="f217b-120">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="f217b-121">Şemayı değiştirir ve isteğe bağlı **msdata: PrimaryKey** öznitelik değerini **true** olarak ayarlarsanız, tabloda benzersiz kısıtlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f217b-121">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="f217b-122">**AllowDBNull** Column özelliği **false** olarak ayarlanır ve kısıtlamanın **IsPrimaryKey** özelliği **true** olarak ayarlanır ve bu sayede **MüşteriNo** sütununu birincil anahtar sütunu yapar.</span><span class="sxs-lookup"><span data-stu-id="f217b-122">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="f217b-123">XML şemasında öğelerin veya özniteliklerin birleşimi üzerinde benzersiz bir kısıtlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f217b-123">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="f217b-124">Aşağıdaki örnek, bir **CustomerID** ve **CompanyName** değerlerinin birleşiminin, şemaya başka bir **xs: Field** öğesi ekleyerek herhangi bir örnekteki tüm **müşteriler** için benzersiz olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f217b-124">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="f217b-125">Bu, sonuçta elde edilen **veri kümesinde** oluşturulan kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="f217b-125">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="f217b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f217b-126">See also</span></span>

- [<span data-ttu-id="f217b-127">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="f217b-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="f217b-128">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f217b-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="f217b-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f217b-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
