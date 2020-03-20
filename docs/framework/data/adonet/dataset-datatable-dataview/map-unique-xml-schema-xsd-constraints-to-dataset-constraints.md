---
title: Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150850"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="fd2d5-102">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="fd2d5-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="fd2d5-103">XML Şema tanım dili (XSD) şemasında, **benzersiz** öğe, bir öğe veya öznitelik teki benzersizlik kısıtlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="fd2d5-104">Bir XML Şemasını ilişkisel şemaya çevirme işleminde, XML Şema'da bir öğe veya öznitelik üzerinde belirtilen benzersiz kısıtlama, oluşturulan <xref:System.Data.DataTable> ilgili <xref:System.Data.DataSet> şemadaki benzersiz bir kısıtlamaya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="fd2d5-105">Aşağıdaki tablo, **benzersiz** öğede belirtebileceğiniz **msdata** özniteliklerini özetleyin.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="fd2d5-106">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="fd2d5-106">Attribute name</span></span>|<span data-ttu-id="fd2d5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd2d5-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fd2d5-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="fd2d5-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="fd2d5-109">Bu öznitelik belirtilirse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="fd2d5-110">Aksi takdirde, **ad** özniteliği kısıtlama adının değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="fd2d5-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="fd2d5-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="fd2d5-112">`PrimaryKey="true"` **Benzersiz** öğede varsa, **doğru**ayarlanmış **IsPrimaryKey** özelliği yle benzersiz bir kısıtlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="fd2d5-113">Aşağıdaki örnekte, benzersiz bir kısıtlama belirtmek için **benzersiz** öğeyi kullanan bir XML Şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="fd2d5-114">Şemadaki **benzersiz** öğe, bir belge örneğindeki tüm **Müşteriler** öğeleri için **CustomerID** alt öğesinin değerinin benzersiz olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="fd2d5-115">**DataSet**oluştururken, eşleme işlemi bu şema okur ve aşağıdaki tabloyu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="fd2d5-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="fd2d5-116">Eşleme işlemi, aşağıdaki **DataSet'te**gösterildiği gibi **CustomerID** sütununda benzersiz bir kısıtlama da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="fd2d5-117">(Basitlik için yalnızca ilgili özellikler gösterilir.)</span><span class="sxs-lookup"><span data-stu-id="fd2d5-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="fd2d5-118">Oluşturulan **DataSet'te,** Benzersiz kısıtlama için **IsPrimaryKey** özelliği **False** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="fd2d5-119">Sütundaki **benzersiz** **özellik, CustomerID** sütun değerlerinin benzersiz olması gerektiğini gösterir (ancak sütunun **AllowDBNull** özelliğinde belirtildiği gibi null bir başvuru olabilir).</span><span class="sxs-lookup"><span data-stu-id="fd2d5-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="fd2d5-120">Şemayı değiştirir ve isteğe bağlı **msdata:PrimaryKey** öznitelik değerini **True**olarak ayarlarsanız, tabloda benzersiz kısıtlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="fd2d5-121">**AllowDBNull** sütun özelliği **False**olarak ayarlanır ve kısıtlamanın **IsPrimaryKey** özelliği **True**olarak ayarlanır ve böylece **CustomerID** sütunu birincil anahtar sütunu haline getirir.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="fd2d5-122">XML Şeması'ndaki öğeler in veya özniteliklerin birleşimi nde benzersiz bir kısıtlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="fd2d5-123">Aşağıdaki örnek, şemaya başka bir **xs:alan** öğesi **ekleyerek, customerID** ve **Şirket Adı** değerlerinin bir birleşiminin herhangi bir durumda tüm **Müşteriler** için benzersiz olması gerektiğini nasıl belirteceğiniz gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="fd2d5-124">Bu, ortaya çıkan **DataSet'te**oluşturulan kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd2d5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd2d5-125">See also</span></span>

- [<span data-ttu-id="fd2d5-126">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="fd2d5-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="fd2d5-127">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd2d5-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="fd2d5-128">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fd2d5-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
