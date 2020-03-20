---
title: Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150941"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="c5016-102">Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="c5016-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="c5016-103">Şemada, **anahtar** öğeyi kullanarak bir öğe veya öznitelik üzerinde önemli bir kısıtlama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5016-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="c5016-104">Anahtar kısıtlamanın belirtildiği öğe veya öznitelik, herhangi bir şema örneğinde benzersiz değerlere sahip olmalıdır ve null değerleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="c5016-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="c5016-105">Anahtar kısıtlaması, anahtar kısıtlamasının tanımlandığı sütunun null değerlere sahip olamayacağı dışında, benzersiz kısıtlamaya benzer.</span><span class="sxs-lookup"><span data-stu-id="c5016-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="c5016-106">Aşağıdaki **tabloda, anahtar** öğede belirtebileceğiniz **msdata** öznitelikleri özetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c5016-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="c5016-107">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="c5016-107">Attribute name</span></span>|<span data-ttu-id="c5016-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5016-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c5016-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="c5016-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="c5016-110">Bu öznitelik belirtilirse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5016-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="c5016-111">Aksi takdirde, **ad** özniteliği kısıtlama adının değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5016-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="c5016-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="c5016-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="c5016-113">Varsa, **IsPrimaryKey** kısıtlama özelliği doğru olarak ayarlanır, böylece birincil anahtar yapma. **true** `PrimaryKey="true"`</span><span class="sxs-lookup"><span data-stu-id="c5016-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="c5016-114">Birincil anahtarların null değerleri olamayacağından **AllowDBNull** sütun özelliği **false**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5016-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="c5016-115">Önemli bir kısıtlamanın belirtildiği şemayı dönüştürmede, eşleme işlemi, kısıtlamadaki her sütun için **yanlış** olarak ayarlanmış **AllowDBNull** sütun özelliğiyle tabloda benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c5016-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="c5016-116">Benzersiz kısıtlamanın **IsPrimaryKey** özelliği, **anahtar** öğeüzerinde belirtilmedikçe `msdata:PrimaryKey="true"` de **false** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5016-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="c5016-117">Bu şema benzersiz bir kısıtlama ile aynıdır `PrimaryKey="true"`hangi .</span><span class="sxs-lookup"><span data-stu-id="c5016-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="c5016-118">Aşağıdaki şema örneğinde, **anahtar** öğe **CustomerID** öğesindeki anahtar kısıtlamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5016-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="c5016-119">**Anahtar** öğe, **Müşteri** öğesinin **CustomerID** alt öğesinin değerlerinin benzersiz değerlere sahip olması ve null değerlere sahip olamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5016-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="c5016-120">XML Şema tanım dili (XSD) şema sını çevirirken, eşleme işlemi aşağıdaki tabloyu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c5016-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="c5016-121">XML Şema eşlemi, aşağıdaki <xref:System.Data.DataSet>gibi **CustomerID** sütununda bir **Benzersiz Kısıtlama** da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c5016-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c5016-122">(Basitlik için yalnızca ilgili özellikler gösterilir.)</span><span class="sxs-lookup"><span data-stu-id="c5016-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="c5016-123">`msdata:PrimaryKey="true"` Oluşturulan **DataSet'te,** şema **anahtar** öğede belirttiği için **UniqueConstraint'in** **IsPrimaryKey** özelliği **doğru** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5016-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="c5016-124">**DataSet'teki** **UniqueConstraint** özelliğinin **Değeri,** şemadaki **anahtar** öğede belirtilen **msdata:ConstraintName** özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="c5016-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5016-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5016-125">See also</span></span>

- [<span data-ttu-id="c5016-126">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="c5016-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="c5016-127">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5016-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="c5016-128">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5016-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
