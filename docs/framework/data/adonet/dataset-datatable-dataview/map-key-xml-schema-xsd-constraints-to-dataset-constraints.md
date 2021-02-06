---
description: 'Hakkında daha fazla bilgi edinin: anahtar XML şeması (XSD) kısıtlamalarını veri kümesi kısıtlamalarına eşleme'
title: Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 0c07b53e06dc6b80395764b2bdd76045ee80bffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651996"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="70bf1-103">Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="70bf1-103">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="70bf1-104">Bir şemada, **anahtar** öğesini kullanarak bir öğe veya öznitelik üzerinde anahtar kısıtlaması belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70bf1-104">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="70bf1-105">Anahtar kısıtlamasının belirtilen öğesi veya özniteliği herhangi bir şema örneğinde benzersiz değerlere sahip olmalı ve null değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="70bf1-105">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="70bf1-106">Anahtar kısıtlaması, anahtar kısıtlamasının tanımlandığı sütunun null değerlere sahip olmadığı durumlar dışında, UNIQUE kısıtlamasına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="70bf1-106">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="70bf1-107">Aşağıdaki tabloda, **anahtar** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="70bf1-107">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="70bf1-108">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="70bf1-108">Attribute name</span></span>|<span data-ttu-id="70bf1-109">Description</span><span class="sxs-lookup"><span data-stu-id="70bf1-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="70bf1-110">**msdata: ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="70bf1-110">**msdata:ConstraintName**</span></span>|<span data-ttu-id="70bf1-111">Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70bf1-111">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="70bf1-112">Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="70bf1-112">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="70bf1-113">**msdata: PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="70bf1-113">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="70bf1-114">Varsa `PrimaryKey="true"` , **IsPrimaryKey** kısıtlama özelliği **true** olarak ayarlanır ve bu sayede birincil anahtar yapılır.</span><span class="sxs-lookup"><span data-stu-id="70bf1-114">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="70bf1-115">**AllowDBNull** Column özelliği **false** olarak ayarlanır, çünkü birincil anahtarlar null değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="70bf1-115">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="70bf1-116">Anahtar kısıtlamasının belirtildiği şemayı dönüştürürken, eşleme işlemi kısıtlamadaki her bir sütun için **AllowDBNull** Column özelliği **false** olarak ayarlanmış tabloda benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70bf1-116">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="70bf1-117">Anahtar öğesinde belirtmediğiniz müddetçe, UNIQUE kısıtlamasının **IsPrimaryKey** özelliği de **false** olarak ayarlanır `msdata:PrimaryKey="true"`  .</span><span class="sxs-lookup"><span data-stu-id="70bf1-117">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="70bf1-118">Bu, şemadaki şema içindeki benzersiz bir kısıtlama ile aynıdır `PrimaryKey="true"` .</span><span class="sxs-lookup"><span data-stu-id="70bf1-118">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="70bf1-119">Aşağıdaki şema örneğinde, **anahtar** öğesi **MüşteriNo** öğesinde anahtar kısıtlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70bf1-119">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="70bf1-120">**Anahtar** öğesi, **Customers** öğesinin **MüşteriNo** alt öğesi değerlerinin benzersiz değerlere sahip olması gerektiğini belirtir ve null değerlere sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="70bf1-120">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="70bf1-121">XML şeması tanım dili (XSD) şemasını çevirirken, eşleme işlemi aşağıdaki tabloyu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="70bf1-121">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="70bf1-122">XML Şeması eşleme, aşağıda gösterildiği gibi **MüşteriNo** sütununda bir **UniqueConstraint kısıtlaması** de oluşturur <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="70bf1-122">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="70bf1-123">(Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)</span><span class="sxs-lookup"><span data-stu-id="70bf1-123">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="70bf1-124">Oluşturulan **veri kümesinde** , şema anahtar öğesinde belirttiğinden **UniqueConstraint** 'in **IsPrimaryKey** özelliği **true** olarak ayarlanır `msdata:PrimaryKey="true"` . </span><span class="sxs-lookup"><span data-stu-id="70bf1-124">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="70bf1-125">**Veri kümesindeki** **uniquekısıtlamasının** **ConstraintName** özelliğinin değeri, şemadaki **anahtar** öğesinde belirtilen **msdata: ConstraintName** özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="70bf1-125">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bf1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70bf1-126">See also</span></span>

- [<span data-ttu-id="70bf1-127">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="70bf1-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="70bf1-128">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="70bf1-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="70bf1-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="70bf1-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
