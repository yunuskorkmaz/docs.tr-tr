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
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme

Bir şemada, **anahtar** öğesini kullanarak bir öğe veya öznitelik üzerinde anahtar kısıtlaması belirtebilirsiniz. Anahtar kısıtlamasının belirtilen öğesi veya özniteliği herhangi bir şema örneğinde benzersiz değerlere sahip olmalı ve null değerlere sahip olamaz.  
  
 Anahtar kısıtlaması, anahtar kısıtlamasının tanımlandığı sütunun null değerlere sahip olmadığı durumlar dışında, UNIQUE kısıtlamasına benzerdir.  
  
 Aşağıdaki tabloda, **anahtar** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.  
  
|Öznitelik adı|Description|  
|--------------------|-----------------|  
|**msdata: ConstraintName**|Bu öznitelik belirtilmişse, değeri kısıtlama adı olarak kullanılır. Aksi takdirde, **Name** özniteliği kısıtlama adının değerini sağlar.|  
|**msdata: PrimaryKey**|Varsa `PrimaryKey="true"` , **IsPrimaryKey** kısıtlama özelliği **true** olarak ayarlanır ve bu sayede birincil anahtar yapılır. **AllowDBNull** Column özelliği **false** olarak ayarlanır, çünkü birincil anahtarlar null değerlere sahip olamaz.|  
  
 Anahtar kısıtlamasının belirtildiği şemayı dönüştürürken, eşleme işlemi kısıtlamadaki her bir sütun için **AllowDBNull** Column özelliği **false** olarak ayarlanmış tabloda benzersiz bir kısıtlama oluşturur. Anahtar öğesinde belirtmediğiniz müddetçe, UNIQUE kısıtlamasının **IsPrimaryKey** özelliği de **false** olarak ayarlanır `msdata:PrimaryKey="true"`  . Bu, şemadaki şema içindeki benzersiz bir kısıtlama ile aynıdır `PrimaryKey="true"` .  
  
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
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML Şeması eşleme, aşağıda gösterildiği gibi **MüşteriNo** sütununda bir **UniqueConstraint kısıtlaması** de oluşturur <xref:System.Data.DataSet> . (Kolaylık sağlaması için yalnızca ilgili özellikler gösterilir.)  
  
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
  
 Oluşturulan **veri kümesinde** , şema anahtar öğesinde belirttiğinden **UniqueConstraint** 'in **IsPrimaryKey** özelliği **true** olarak ayarlanır `msdata:PrimaryKey="true"` .   
  
 **Veri kümesindeki** **uniquekısıtlamasının** **ConstraintName** özelliğinin değeri, şemadaki **anahtar** öğesinde belirtilen **msdata: ConstraintName** özniteliğinin değeridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
