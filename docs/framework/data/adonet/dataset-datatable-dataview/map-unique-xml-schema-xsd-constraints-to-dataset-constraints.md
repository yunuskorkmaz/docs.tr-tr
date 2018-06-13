---
title: Veri kümesi sınırlamaları benzersiz XML Şeması (XSD) kısıtlamalar eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8aed9830d613eeb7d49d2339a8ac1892c0e28e93
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761174"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="a7a33-102">Veri kümesi sınırlamaları benzersiz XML Şeması (XSD) kısıtlamalar eşleme</span><span class="sxs-lookup"><span data-stu-id="a7a33-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="a7a33-103">Bir XML Şeması Tanım Dili (XSD) şemasında **benzersiz** öğesi bir öğe veya öznitelik benzersizlik kısıtlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7a33-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="a7a33-104">Bir XML Şeması ilişkisel bir şemaya çevirme sürecinde, öğe veya öznitelik XML şemasında belirtilen UNIQUE kısıtlaması benzersiz bir kısıtlamaya eşlenmiş <xref:System.Data.DataTable> karşılık gelen <xref:System.Data.DataSet> , oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a7a33-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="a7a33-105">Aşağıdaki tabloda ana hatlarını **msdata** belirleyebilirsiniz öznitelikleri **benzersiz** öğesi.</span><span class="sxs-lookup"><span data-stu-id="a7a33-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="a7a33-106">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="a7a33-106">Attribute name</span></span>|<span data-ttu-id="a7a33-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a33-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a7a33-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="a7a33-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="a7a33-109">Bu öznitelik belirtilen değeri kısıtlama adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7a33-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="a7a33-110">Aksi takdirde, **adı** özniteliği, kısıtlama adı değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7a33-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="a7a33-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="a7a33-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="a7a33-112">Varsa `PrimaryKey="true"` bulunur **benzersiz** öğesi, benzersiz kısıtlamayı oluşturulur **IsPrimaryKey** özelliğini **doğru**.</span><span class="sxs-lookup"><span data-stu-id="a7a33-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="a7a33-113">Aşağıdaki örnek kullanan bir XML şeması gösterir **benzersiz** benzersizlik kısıtlamasını belirtmek amacıyla öğesi.</span><span class="sxs-lookup"><span data-stu-id="a7a33-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="a7a33-114">**Benzersiz** schema öğesinde belirtir, tüm **müşteriler** bir belgedeki öğeleri örneği, değeri **CustomerID** alt öğesi benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7a33-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="a7a33-115">Binada **DataSet**, eşleme işlemi bu şemayı okur ve aşağıdaki tabloda oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a7a33-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="a7a33-116">Eşleme işlemini de UNIQUE kısıtlaması oluşturur **CustomerID** aşağıda gösterildiği gibi sütun **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a7a33-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="a7a33-117">(Kolaylık sağlamak için yalnızca ilgili özellikleri gösterilir.)</span><span class="sxs-lookup"><span data-stu-id="a7a33-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="a7a33-118">İçinde **DataSet** , oluşturulduğunda, **IsPrimaryKey** özelliği ayarlanmış **False** UNIQUE kısıtlaması için.</span><span class="sxs-lookup"><span data-stu-id="a7a33-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="a7a33-119">**Benzersiz** sütun özellikte gösterir **CustomerID** sütun değerleri benzersiz olmalıdır (ancak belirtildiği gibi bir null başvuru olabilir **AllowDBNull** özelliği sütun).</span><span class="sxs-lookup"><span data-stu-id="a7a33-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="a7a33-120">İçin şemayı ve isteğe bağlı ayarlarsanız **MSDATA** öznitelik değeri için **doğru**, benzersiz kısıtlamayı tablo üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a7a33-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="a7a33-121">**AllowDBNull** column özelliği ayarlanmış **False**ve **IsPrimaryKey** özellik kümesine kısıtlamasının **doğru**, böylece yapmayı **CustomerID** sütun birincil anahtar sütunu.</span><span class="sxs-lookup"><span data-stu-id="a7a33-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="a7a33-122">XML Şeması öğelerini veya öznitelikleri birleşimi benzersiz bir kısıtlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7a33-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="a7a33-123">Aşağıdaki örnek, belirtmek bir birleşimini gösterilmiştir **CustomerID** ve **ŞirketAdı** değerleri tümü için benzersiz olmalıdır **müşteriler** herhangi bir örneğindeki tarafından başka bir ekleme **xs:field** schema öğesinde.</span><span class="sxs-lookup"><span data-stu-id="a7a33-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="a7a33-124">Bu sonuç olarak oluşturulan sınırlamadır **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a7a33-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7a33-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7a33-125">See Also</span></span>  
 [<span data-ttu-id="a7a33-126">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="a7a33-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="a7a33-127">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7a33-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="a7a33-128">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a7a33-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
