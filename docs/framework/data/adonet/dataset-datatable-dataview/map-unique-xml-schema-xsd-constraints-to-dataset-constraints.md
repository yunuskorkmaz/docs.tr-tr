---
title: Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 231f23ccf47f60b902fdd5c66b63fe1a750445f9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203419"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="26c0a-102">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="26c0a-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="26c0a-103">Bir XML şeması tanım dili (XSD) şemasında, **Unique** öğesi bir öğe veya öznitelik üzerinde benzersizlik kısıtlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="26c0a-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="26c0a-104">Bir XML şemasını ilişkisel bir şemaya çevirme işleminde, XML şemasında bir öğe veya öznitelik üzerinde belirtilen benzersiz kısıtlama, <xref:System.Data.DataTable> karşılık gelen <xref:System.Data.DataSet> ' de bulunan içinde benzersiz bir kısıtlamaya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="26c0a-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="26c0a-105">Aşağıdaki tabloda, **benzersiz** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="26c0a-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="26c0a-106">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="26c0a-106">Attribute name</span></span>|<span data-ttu-id="26c0a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c0a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="26c0a-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="26c0a-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="26c0a-109">Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26c0a-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="26c0a-110">Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="26c0a-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="26c0a-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="26c0a-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="26c0a-112">Unique öğesinde varsa, **IsPrimaryKey** özelliği **true**olarak ayarlanan bir Unique kısıtlaması oluşturulur. `PrimaryKey="true"`</span><span class="sxs-lookup"><span data-stu-id="26c0a-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="26c0a-113">Aşağıdaki örnek, bir benzersizlik kısıtlaması belirtmek için **benzersiz** öğe kullanan bir XML şeması gösterir.</span><span class="sxs-lookup"><span data-stu-id="26c0a-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="26c0a-114">Şemadaki **benzersiz** öğe, bir belge örneğindeki tüm **müşteriler** öğeleri için, **MüşteriNo** alt öğesinin değerinin benzersiz olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26c0a-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="26c0a-115">**Veri kümesini**oluştururken, eşleme işlemi bu şemayı okur ve aşağıdaki tabloyu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="26c0a-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="26c0a-116">Eşleme işlemi, aşağıdaki **veri kümesinde**gösterildiği gibi **MüşteriNo** sütununda de benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26c0a-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="26c0a-117">(Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)</span><span class="sxs-lookup"><span data-stu-id="26c0a-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
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
  
 <span data-ttu-id="26c0a-118">Oluşturulan **veri kümesinde** , **IsPrimaryKey** özelliği, Unique kısıtlaması için **false** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="26c0a-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="26c0a-119">Sütunundaki **UNIQUE** özelliği, **MüşteriNo** sütun değerlerinin benzersiz olması gerektiğini belirtir (ancak sütunun **AllowDBNull** özelliği tarafından belirtilen şekilde null bir başvuru olabilir).</span><span class="sxs-lookup"><span data-stu-id="26c0a-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="26c0a-120">Şemayı değiştirir ve isteğe bağlı **msdata: PrimaryKey** öznitelik değerini **true**olarak ayarlarsanız, tabloda benzersiz kısıtlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="26c0a-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="26c0a-121">**AllowDBNull** Column özelliği **false**olarak ayarlanır ve kısıtlamanın **IsPrimaryKey** özelliği **true**olarak ayarlanır ve bu sayede **MüşteriNo** sütununu birincil anahtar sütunu yapar.</span><span class="sxs-lookup"><span data-stu-id="26c0a-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="26c0a-122">XML şemasında öğelerin veya özniteliklerin birleşimi üzerinde benzersiz bir kısıtlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26c0a-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="26c0a-123">Aşağıdaki örnek, bir **CustomerID** ve **CompanyName** değerlerinin birleşiminin, şemaya başka bir **xs: Field** öğesi ekleyerek herhangi bir örnekteki tüm **müşteriler** için benzersiz olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26c0a-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="26c0a-124">Bu, sonuçta elde edilen **veri kümesinde**oluşturulan kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="26c0a-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="26c0a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26c0a-125">See also</span></span>

- [<span data-ttu-id="26c0a-126">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="26c0a-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="26c0a-127">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="26c0a-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="26c0a-128">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="26c0a-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
