---
title: Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 650cd6b8b8149529f115f22a11d19178fbd6d302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785380"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="d3cb4-102">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="d3cb4-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="d3cb4-103">Bir XML Şeması Tanım Dili (XSD) şemaya içinde **benzersiz** öğe, öğe veya öznitelik benzersizlik kısıtlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="d3cb4-104">Bir XML şeması bir ilişkisel şemasına çevirme sürecinde, benzersiz bir kısıtlamaya bir öğe veya öznitelik XML şemasında belirtilen UNIQUE kısıtlaması eşlenir <xref:System.Data.DataTable> karşılık gelen <xref:System.Data.DataSet> , oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="d3cb4-105">Aşağıdaki tabloda ana hatlarını **msdata** belirleyebilirsiniz öznitelikleri **benzersiz** öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="d3cb4-106">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="d3cb4-106">Attribute name</span></span>|<span data-ttu-id="d3cb4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3cb4-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d3cb4-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="d3cb4-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="d3cb4-109">Bu öznitelik belirtilmezse, değeri kısıtlama adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="d3cb4-110">Aksi takdirde, **adı** özniteliği kısıtlama adı değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="d3cb4-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="d3cb4-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="d3cb4-112">Varsa `PrimaryKey="true"` bulunan **benzersiz** öğesi benzersiz kısıtlama ile oluşturulur **IsPrimaryKey** özelliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="d3cb4-113">Kullanan bir XML Şeması aşağıdaki örnekte **benzersiz** benzersizlik kısıtlamasını belirtmek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="d3cb4-114">**Benzersiz** şema öğesi belirtir, tüm **müşteriler** bir belgedeki öğeler örneği, değerini **CustomerID** alt öğesi benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="d3cb4-115">Binada **veri kümesi**, eşleme işlemi bu şemayı okur ve aşağıdaki tabloda oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d3cb4-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="d3cb4-116">Eşleme işlemi aynı zamanda benzersiz kısıtlama oluşturur **CustomerID** sütun, aşağıda gösterildiği gibi **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="d3cb4-117">(Kolaylık olması için yalnızca ilgili özellikleri gösterilmektedir.)</span><span class="sxs-lookup"><span data-stu-id="d3cb4-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="d3cb4-118">İçinde **veri kümesi** , oluşturulduğunda, **IsPrimaryKey** özelliği **False** benzersiz kısıtlama için.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="d3cb4-119">**Benzersiz** özelliğini gösterir **CustomerID** sütun değerleri benzersiz olmalıdır (ancak bunlar tarafından belirtilen bir null başvuru olabilir **AllowDBNull** Özellik sütununun).</span><span class="sxs-lookup"><span data-stu-id="d3cb4-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="d3cb4-120">Şemayı değiştirmek ve isteğe bağlı **MSDATA** öznitelik değerine **True**, benzersiz kısıtlamayı tablo üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="d3cb4-121">**AllowDBNull** column özelliği ayarlandığında **False**ve **IsPrimaryKey** özellik kümesine kısıtlamasının **True**, bu nedenle yapmayı **CustomerID** sütun birincil anahtar sütunu.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="d3cb4-122">XML şemasında öğeler veya öznitelikleri birleşimi benzersiz kısıtlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="d3cb4-123">Aşağıdaki örnek bir birleşimi belirtme yapmayı gösteren **CustomerID** ve **CompanyName** değerleri tüm benzersiz olmalıdır **müşteriler** herhangi bir örneğindeki tarafından eklemeden **xs:field** şema öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="d3cb4-124">Bu sonuç olarak oluşturulan sınırlamadır **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3cb4-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3cb4-125">See also</span></span>

- [<span data-ttu-id="d3cb4-126">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="d3cb4-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="d3cb4-127">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3cb4-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="d3cb4-128">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d3cb4-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
