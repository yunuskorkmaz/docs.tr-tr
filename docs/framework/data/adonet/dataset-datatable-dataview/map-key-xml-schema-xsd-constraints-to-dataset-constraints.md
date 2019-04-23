---
title: Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 46a980f06198c6f06bb13824c65cfb5309eec154
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189924"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
Şemada, bir öğenin anahtar kısıtlaması belirtebilir veya özniteliğini kullanarak **anahtar** öğesi. Öğe veya öznitelik bir anahtar kısıtlaması belirtilen şema örnek benzersiz değerlere sahip olmalıdır ve null değer olamaz.  
  
 Anahtar kısıtlaması, bir anahtar kısıtlaması tanımlandığı sütunu null değerler alamaz dışında benzersiz kısıtlama için benzerdir.  
  
 Aşağıdaki tabloda ana hatlarını **msdata** belirleyebilirsiniz öznitelikleri **anahtar** öğesi.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Bu öznitelik belirtilmezse, değeri kısıtlama adı kullanılır. Aksi takdirde, **adı** özniteliği kısıtlama adı değerini sağlar.|  
|**msdata:PrimaryKey**|Varsa `PrimaryKey="true"` var, **IsPrimaryKey** kısıtlaması özelliği **true**, bu nedenle birincil anahtar kolaylaştırır. **AllowDBNull** column özelliği ayarlandığında **false**, birincil anahtarlar null değerler olamaz.|  
  
 Bir anahtar kısıtlaması belirtilirse şema dönüştürmek eşleme işlemi ile tablosunda benzersiz kısıtlama oluşturur **AllowDBNull** column özelliği ayarlanmış **false** her sütun için kısıtlama. **IsPrimaryKey** de UNIQUE kısıtlaması özelliği ayarlanmış **false** belirtmiş olduğunuz sürece `msdata:PrimaryKey="true"` üzerinde **anahtar** öğesi. Bu kısıtlama, şemada aynıdır `PrimaryKey="true"`.  
  
 Aşağıdaki şema örnekte **anahtarı** öğesi üzerinde anahtar kısıtlaması belirtir **CustomerID** öğesi.  
  
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
  
 **Anahtarı** öğesi belirtir değerlerini **CustomerID** alt öğesi **müşteriler** öğesi benzersiz değerlere sahip olmalıdır ve null değer olamaz. XML Şeması Tanım Dili (XSD) şemaya çevirme aşağıdaki tabloda eşleme işlemi oluşturur:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML şema eşleme ayrıca oluşturur bir **UniqueConstraint** üzerinde **CustomerID** sütun, aşağıda gösterildiği gibi <xref:System.Data.DataSet>. (Kolaylık olması için yalnızca ilgili özellikleri gösterilmektedir.)  
  
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
  
 İçinde **veri kümesi** , oluşturulduğunda, **IsPrimaryKey** özelliği **UniqueConstraint** ayarlanır **true** çünkü şeması belirtir `msdata:PrimaryKey="true"` içinde **anahtar** öğesi.  
  
 Değerini **ConstraintName** özelliği **UniqueConstraint** içinde **veri kümesi** değeri **msdata:ConstraintName** Belirtilen öznitelik **anahtar** şema öğesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
