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
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
XML Şema tanım dili (XSD) şemasında, **benzersiz** öğe, bir öğe veya öznitelik teki benzersizlik kısıtlamasını belirtir. Bir XML Şemasını ilişkisel şemaya çevirme işleminde, XML Şema'da bir öğe veya öznitelik üzerinde belirtilen benzersiz kısıtlama, oluşturulan <xref:System.Data.DataTable> ilgili <xref:System.Data.DataSet> şemadaki benzersiz bir kısıtlamaya eşlenir.  
  
 Aşağıdaki tablo, **benzersiz** öğede belirtebileceğiniz **msdata** özniteliklerini özetleyin.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Bu öznitelik belirtilirse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **ad** özniteliği kısıtlama adının değerini sağlar.|  
|**msdata:PrimaryKey**|`PrimaryKey="true"` **Benzersiz** öğede varsa, **doğru**ayarlanmış **IsPrimaryKey** özelliği yle benzersiz bir kısıtlama oluşturulur.|  
  
 Aşağıdaki örnekte, benzersiz bir kısıtlama belirtmek için **benzersiz** öğeyi kullanan bir XML Şeması gösterilmektedir.  
  
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
  
 Şemadaki **benzersiz** öğe, bir belge örneğindeki tüm **Müşteriler** öğeleri için **CustomerID** alt öğesinin değerinin benzersiz olması gerektiğini belirtir. **DataSet**oluştururken, eşleme işlemi bu şema okur ve aşağıdaki tabloyu oluşturur:  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Eşleme işlemi, aşağıdaki **DataSet'te**gösterildiği gibi **CustomerID** sütununda benzersiz bir kısıtlama da oluşturur. (Basitlik için yalnızca ilgili özellikler gösterilir.)  
  
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
  
 Oluşturulan **DataSet'te,** Benzersiz kısıtlama için **IsPrimaryKey** özelliği **False** olarak ayarlanır. Sütundaki **benzersiz** **özellik, CustomerID** sütun değerlerinin benzersiz olması gerektiğini gösterir (ancak sütunun **AllowDBNull** özelliğinde belirtildiği gibi null bir başvuru olabilir).  
  
 Şemayı değiştirir ve isteğe bağlı **msdata:PrimaryKey** öznitelik değerini **True**olarak ayarlarsanız, tabloda benzersiz kısıtlama oluşturulur. **AllowDBNull** sütun özelliği **False**olarak ayarlanır ve kısıtlamanın **IsPrimaryKey** özelliği **True**olarak ayarlanır ve böylece **CustomerID** sütunu birincil anahtar sütunu haline getirir.  
  
 XML Şeması'ndaki öğeler in veya özniteliklerin birleşimi nde benzersiz bir kısıtlama belirtebilirsiniz. Aşağıdaki örnek, şemaya başka bir **xs:alan** öğesi **ekleyerek, customerID** ve **Şirket Adı** değerlerinin bir birleşiminin herhangi bir durumda tüm **Müşteriler** için benzersiz olması gerektiğini nasıl belirteceğiniz gösterilebilir.  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 Bu, ortaya çıkan **DataSet'te**oluşturulan kısıtlamadır.  
  
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
