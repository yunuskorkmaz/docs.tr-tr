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
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
Şemada, **anahtar** öğeyi kullanarak bir öğe veya öznitelik üzerinde önemli bir kısıtlama belirtebilirsiniz. Anahtar kısıtlamanın belirtildiği öğe veya öznitelik, herhangi bir şema örneğinde benzersiz değerlere sahip olmalıdır ve null değerleri olamaz.  
  
 Anahtar kısıtlaması, anahtar kısıtlamasının tanımlandığı sütunun null değerlere sahip olamayacağı dışında, benzersiz kısıtlamaya benzer.  
  
 Aşağıdaki **tabloda, anahtar** öğede belirtebileceğiniz **msdata** öznitelikleri özetlenebilir.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Bu öznitelik belirtilirse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **ad** özniteliği kısıtlama adının değerini sağlar.|  
|**msdata:PrimaryKey**|Varsa, **IsPrimaryKey** kısıtlama özelliği doğru olarak ayarlanır, böylece birincil anahtar yapma. **true** `PrimaryKey="true"` Birincil anahtarların null değerleri olamayacağından **AllowDBNull** sütun özelliği **false**olarak ayarlanır.|  
  
 Önemli bir kısıtlamanın belirtildiği şemayı dönüştürmede, eşleme işlemi, kısıtlamadaki her sütun için **yanlış** olarak ayarlanmış **AllowDBNull** sütun özelliğiyle tabloda benzersiz bir kısıtlama oluşturur. Benzersiz kısıtlamanın **IsPrimaryKey** özelliği, **anahtar** öğeüzerinde belirtilmedikçe `msdata:PrimaryKey="true"` de **false** olarak ayarlanır. Bu şema benzersiz bir kısıtlama ile aynıdır `PrimaryKey="true"`hangi .  
  
 Aşağıdaki şema örneğinde, **anahtar** öğe **CustomerID** öğesindeki anahtar kısıtlamayı belirtir.  
  
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
  
 **Anahtar** öğe, **Müşteri** öğesinin **CustomerID** alt öğesinin değerlerinin benzersiz değerlere sahip olması ve null değerlere sahip olamayacağını belirtir. XML Şema tanım dili (XSD) şema sını çevirirken, eşleme işlemi aşağıdaki tabloyu oluşturur:  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML Şema eşlemi, aşağıdaki <xref:System.Data.DataSet>gibi **CustomerID** sütununda bir **Benzersiz Kısıtlama** da oluşturur. (Basitlik için yalnızca ilgili özellikler gösterilir.)  
  
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
  
 `msdata:PrimaryKey="true"` Oluşturulan **DataSet'te,** şema **anahtar** öğede belirttiği için **UniqueConstraint'in** **IsPrimaryKey** özelliği **doğru** olarak ayarlanır.  
  
 **DataSet'teki** **UniqueConstraint** özelliğinin **Değeri,** şemadaki **anahtar** öğede belirtilen **msdata:ConstraintName** özniteliğinin değeridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
