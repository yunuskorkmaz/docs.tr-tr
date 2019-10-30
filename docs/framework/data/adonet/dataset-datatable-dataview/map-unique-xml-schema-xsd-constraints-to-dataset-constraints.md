---
title: Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 6b847aba31aa75f7be3bd6a11b6bcb8231c06bc4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040358"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="e5745-102">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5745-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="e5745-103">Bir XML şeması tanım dili (XSD) şemasında, **Unique** öğesi bir öğe veya öznitelik üzerinde benzersizlik kısıtlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5745-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="e5745-104">Bir XML şemasını ilişkisel bir şemaya çevirme işleminde, XML şemasında bir öğe veya öznitelik üzerinde belirtilen benzersiz kısıtlama, oluşturulan karşılık gelen <xref:System.Data.DataSet> <xref:System.Data.DataTable> benzersiz bir kısıtlamaya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e5745-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="e5745-105">Aşağıdaki tabloda, **benzersiz** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5745-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="e5745-106">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="e5745-106">Attribute name</span></span>|<span data-ttu-id="e5745-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5745-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e5745-108">**msdata: ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="e5745-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="e5745-109">Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5745-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="e5745-110">Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5745-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="e5745-111">**msdata: PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="e5745-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="e5745-112">**Benzersiz** öğede `PrimaryKey="true"` varsa, **ıprimarykey** özelliği **true**olarak ayarlanan bir Unique kısıtlaması oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5745-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="e5745-113">Aşağıdaki örnek, bir benzersizlik kısıtlaması belirtmek için **benzersiz** öğe kullanan bir XML şeması gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5745-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="e5745-114">Şemadaki **benzersiz** öğe, bir belge örneğindeki tüm **müşteriler** öğeleri için, **MüşteriNo** alt öğesinin değerinin benzersiz olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5745-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="e5745-115">**Veri kümesini**oluştururken, eşleme işlemi bu şemayı okur ve aşağıdaki tabloyu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e5745-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="e5745-116">Eşleme işlemi, aşağıdaki **veri kümesinde**gösterildiği gibi **MüşteriNo** sütununda de benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5745-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="e5745-117">(Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)</span><span class="sxs-lookup"><span data-stu-id="e5745-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="e5745-118">Oluşturulan **veri kümesinde** , **IsPrimaryKey** özelliği, Unique kısıtlaması için **false** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e5745-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="e5745-119">Sütunundaki **UNIQUE** özelliği, **MüşteriNo** sütun değerlerinin benzersiz olması gerektiğini belirtir (ancak sütunun **AllowDBNull** özelliği tarafından belirtilen şekilde null bir başvuru olabilir).</span><span class="sxs-lookup"><span data-stu-id="e5745-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="e5745-120">Şemayı değiştirir ve isteğe bağlı **msdata: PrimaryKey** öznitelik değerini **true**olarak ayarlarsanız, tabloda benzersiz kısıtlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5745-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="e5745-121">**AllowDBNull** Column özelliği **false**olarak ayarlanır ve kısıtlamanın **IsPrimaryKey** özelliği **true**olarak ayarlanır ve bu sayede **MüşteriNo** sütununu birincil anahtar sütunu yapar.</span><span class="sxs-lookup"><span data-stu-id="e5745-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="e5745-122">XML şemasında öğelerin veya özniteliklerin birleşimi üzerinde benzersiz bir kısıtlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5745-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="e5745-123">Aşağıdaki örnek, bir **CustomerID** ve **CompanyName** değerlerinin birleşiminin, şemaya başka bir **xs: Field** öğesi ekleyerek herhangi bir örnekteki tüm **müşteriler** için benzersiz olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5745-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="e5745-124">Bu, sonuçta elde edilen **veri kümesinde**oluşturulan kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="e5745-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5745-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5745-125">See also</span></span>

- [<span data-ttu-id="e5745-126">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5745-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="e5745-127">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5745-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="e5745-128">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5745-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
