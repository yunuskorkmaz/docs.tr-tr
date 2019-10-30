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
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
Bir XML şeması tanım dili (XSD) şemasında, **Unique** öğesi bir öğe veya öznitelik üzerinde benzersizlik kısıtlamasını belirtir. Bir XML şemasını ilişkisel bir şemaya çevirme işleminde, XML şemasında bir öğe veya öznitelik üzerinde belirtilen benzersiz kısıtlama, oluşturulan karşılık gelen <xref:System.Data.DataSet> <xref:System.Data.DataTable> benzersiz bir kısıtlamaya eşlenir.  
  
 Aşağıdaki tabloda, **benzersiz** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata: ConstraintName**|Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.|  
|**msdata: PrimaryKey**|**Benzersiz** öğede `PrimaryKey="true"` varsa, **ıprimarykey** özelliği **true**olarak ayarlanan bir Unique kısıtlaması oluşturulur.|  
  
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
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Eşleme işlemi, aşağıdaki **veri kümesinde**gösterildiği gibi **MüşteriNo** sütununda de benzersiz bir kısıtlama oluşturur. (Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)  
  
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
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
