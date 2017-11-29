---
title: "Harita anahtar DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f5247d0ccfd2ceec641ff29d29b889a55c1a5e12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Harita anahtar DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları
Şemada, bir öğenin anahtar kısıtlaması belirtin veya kullanarak öznitelik **anahtar** öğesi. Öğesi veya özniteliği bir anahtar kısıtlaması belirtilen şema örnek benzersiz değerlere sahip olmalıdır ve null değerler olamaz.  
  
 Bir anahtar kısıtlaması tanımlandığı sütunu null değerler olamaz anahtar kısıtlaması benzersiz kısıtlama benzerdir.  
  
 Aşağıdaki tabloda ana hatlarını **msdata** belirleyebilirsiniz öznitelikleri **anahtar** öğesi.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**MSDATA:ConstraintName**|Bu öznitelik belirtilen değeri kısıtlama adı kullanılır. Aksi takdirde, **adı** özniteliği, kısıtlama adı değerini sağlar.|  
|**MSDATA**|Varsa `PrimaryKey="true"` var, **IsPrimaryKey** kısıtlaması özelliği ayarlanmış **doğru**, böylece birincil anahtar yapma. **AllowDBNull** column özelliği ayarlanmış **yanlış**, birincil anahtarlar null değerler olamaz.|  
  
 Bir anahtar kısıtlaması belirtilmişse şema dönüştürülmesi kapsamında, eşleme işlemi tablo ile birlikte benzersiz bir kısıtlama oluşturur **AllowDBNull** sütun özelliğinin ayarlandığı **false** her sütun için kısıtlama. **IsPrimaryKey** de UNIQUE kısıtlaması özelliği ayarlanmış **false** belirttiğiniz sürece `msdata:PrimaryKey="true"` üzerinde **anahtar** öğesi. Bu kısıtlama, şemasında aynıdır `PrimaryKey="true"`.  
  
 Aşağıdaki şema örnekte **anahtar** öğesi belirtir anahtar kısıtlaması **CustomerID** öğesi.  
  
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
  
 **Anahtar** öğesi belirttiğinden değerlerini **CustomerID** alt öğesi olan **müşteriler** öğesi benzersiz değerlere sahip olmalıdır ve null değerler olamaz. XML Şeması Tanım Dili (XSD) şeması çevirme içinde eşleme işlemi aşağıdaki tabloda oluşturur:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML şema eşleme da oluşturur bir **UniqueConstraint** üzerinde **CustomerID** sütun, aşağıda gösterildiği gibi <xref:System.Data.DataSet>. (Kolaylık sağlamak için yalnızca ilgili özellikleri gösterilir.)  
  
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
  
 İçinde **DataSet** , oluşturulduğunda, **IsPrimaryKey** özelliği **UniqueConstraint** ayarlanır **true** çünkü şeması belirtir `msdata:PrimaryKey="true"` içinde **anahtar** öğesi.  
  
 Değeri **ConstraintName** özelliği **UniqueConstraint** içinde **DataSet** değeri **msdata:ConstraintName** Belirtilen öznitelik **anahtar** schema öğesinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri kümesi sınırlamaları için eşleme XML Şeması (XSD) kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [DataSet ilişkileri XML Schema (XSD) oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
