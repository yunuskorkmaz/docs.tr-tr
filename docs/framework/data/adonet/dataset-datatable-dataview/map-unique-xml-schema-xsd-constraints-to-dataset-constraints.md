---
title: Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 4aa94dfaf088a2a934c8901e2720f166d3a38dae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784414"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
Bir XML şeması tanım dili (XSD) şemasında, **Unique** öğesi bir öğe veya öznitelik üzerinde benzersizlik kısıtlamasını belirtir. Bir XML şemasını ilişkisel bir şemaya çevirme işleminde, XML şemasında bir öğe veya öznitelik üzerinde belirtilen benzersiz kısıtlama, <xref:System.Data.DataTable> karşılık gelen <xref:System.Data.DataSet> ' de bulunan içinde benzersiz bir kısıtlamaya eşlenir.  
  
 Aşağıdaki tabloda, **benzersiz** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.|  
|**msdata:PrimaryKey**|Unique öğesinde varsa, **IsPrimaryKey** özelliği **true**olarak ayarlanan bir Unique kısıtlaması oluşturulur. `PrimaryKey="true"`|  
  
 Aşağıdaki örnek, bir benzersizlik kısıtlaması belirtmek için **benzersiz** öğe kullanan bir XML şeması gösterir.  
  
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
  
 Şemadaki **benzersiz** öğe, bir belge örneğindeki tüm **müşteriler** öğeleri için, **MüşteriNo** alt öğesinin değerinin benzersiz olması gerektiğini belirtir. **Veri kümesini**oluştururken, eşleme işlemi bu şemayı okur ve aşağıdaki tabloyu oluşturur:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Eşleme işlemi, aşağıdaki **veri kümesinde**gösterildiği gibi **MüşteriNo** sütununda de benzersiz bir kısıtlama oluşturur. (Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)  
  
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
  
 Oluşturulan **veri kümesinde** , **IsPrimaryKey** özelliği, Unique kısıtlaması için **false** olarak ayarlanır. Sütunundaki **UNIQUE** özelliği, **MüşteriNo** sütun değerlerinin benzersiz olması gerektiğini belirtir (ancak sütunun **AllowDBNull** özelliği tarafından belirtilen şekilde null bir başvuru olabilir).  
  
 Şemayı değiştirir ve isteğe bağlı **msdata: PrimaryKey** öznitelik değerini **true**olarak ayarlarsanız, tabloda benzersiz kısıtlama oluşturulur. **AllowDBNull** Column özelliği **false**olarak ayarlanır ve kısıtlamanın **IsPrimaryKey** özelliği **true**olarak ayarlanır ve bu sayede **MüşteriNo** sütununu birincil anahtar sütunu yapar.  
  
 XML şemasında öğelerin veya özniteliklerin birleşimi üzerinde benzersiz bir kısıtlama belirtebilirsiniz. Aşağıdaki örnek, bir **CustomerID** ve **CompanyName** değerlerinin birleşiminin, şemaya başka bir **xs: Field** öğesi ekleyerek herhangi bir örnekteki tüm **müşteriler** için benzersiz olması gerektiğini belirtir.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Bu, sonuçta elde edilen **veri kümesinde**oluşturulan kısıtlamadır.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
