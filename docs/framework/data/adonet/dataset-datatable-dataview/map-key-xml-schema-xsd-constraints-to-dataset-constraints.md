---
title: Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: d6fcdae77c2f2ac07ea5cd16baf07cd5de36d25b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203471"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
Bir şemada, **anahtar** öğesini kullanarak bir öğe veya öznitelik üzerinde anahtar kısıtlaması belirtebilirsiniz. Anahtar kısıtlamasının belirtilen öğesi veya özniteliği herhangi bir şema örneğinde benzersiz değerlere sahip olmalı ve null değerlere sahip olamaz.  
  
 Anahtar kısıtlaması, anahtar kısıtlamasının tanımlandığı sütunun null değerlere sahip olmadığı durumlar dışında, UNIQUE kısıtlamasına benzerdir.  
  
 Aşağıdaki tabloda, **anahtar** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.|  
|**msdata:PrimaryKey**|Varsa `PrimaryKey="true"` , **IsPrimaryKey** kısıtlama özelliği **true**olarak ayarlanır ve bu sayede birincil anahtar yapılır. **AllowDBNull** Column özelliği **false**olarak ayarlanır, çünkü birincil anahtarlar null değerlere sahip olamaz.|  
  
 Anahtar kısıtlamasının belirtildiği şemayı dönüştürürken, eşleme işlemi kısıtlamadaki her bir sütun için **AllowDBNull** Column özelliği **false** olarak ayarlanmış tabloda benzersiz bir kısıtlama oluşturur. **Anahtar** öğesinde `msdata:PrimaryKey="true"` belirtmediğiniz müddetçe, UNIQUE kısıtlamasının **IsPrimaryKey** özelliği de **false** olarak ayarlanır. Bu, şemadaki şema `PrimaryKey="true"`içindeki benzersiz bir kısıtlama ile aynıdır.  
  
 Aşağıdaki şema örneğinde, **anahtar** öğesi **MüşteriNo** öğesinde anahtar kısıtlamasını belirtir.  
  
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
  
 **Anahtar** öğesi, **Customers** öğesinin **MüşteriNo** alt öğesi değerlerinin benzersiz değerlere sahip olması gerektiğini belirtir ve null değerlere sahip olamaz. XML şeması tanım dili (XSD) şemasını çevirirken, eşleme işlemi aşağıdaki tabloyu oluşturur:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML Şeması eşleme, aşağıda <xref:System.Data.DataSet>gösterildiği gibi **MüşteriNo** sütununda bir **UniqueConstraint kısıtlaması** de oluşturur. (Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)  
  
```  
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
  
 Oluşturulan **veri kümesinde** , şema **anahtar** öğesinde belirttiğinden `msdata:PrimaryKey="true"` **UniqueConstraint** 'in **IsPrimaryKey** özelliği **true** olarak ayarlanır.  
  
 **Veri kümesindeki** **uniquekısıtlamasının** **ConstraintName** özelliğinin değeri, şemadaki **anahtar** öğesinde belirtilen **msdata: ConstraintName** özniteliğinin değeridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
