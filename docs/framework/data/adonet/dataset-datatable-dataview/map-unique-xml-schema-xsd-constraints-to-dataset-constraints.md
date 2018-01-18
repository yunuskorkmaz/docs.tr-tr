---
title: "Veri kümesi sınırlamaları benzersiz XML Şeması (XSD) kısıtlamalar eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3700e4010176abed05677043469476fe34cd564c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Veri kümesi sınırlamaları benzersiz XML Şeması (XSD) kısıtlamalar eşleme
Bir XML Şeması Tanım Dili (XSD) şemasında **benzersiz** öğesi bir öğe veya öznitelik benzersizlik kısıtlamasını belirtir. Bir XML Şeması ilişkisel bir şemaya çevirme sürecinde, öğe veya öznitelik XML şemasında belirtilen UNIQUE kısıtlaması benzersiz bir kısıtlamaya eşlenmiş <xref:System.Data.DataTable> karşılık gelen <xref:System.Data.DataSet> , oluşturulur.  
  
 Aşağıdaki tabloda ana hatlarını **msdata** belirleyebilirsiniz öznitelikleri **benzersiz** öğesi.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Bu öznitelik belirtilen değeri kısıtlama adı kullanılır. Aksi takdirde, **adı** özniteliği, kısıtlama adı değerini sağlar.|  
|**msdata:PrimaryKey**|Varsa `PrimaryKey="true"` bulunur **benzersiz** öğesi, benzersiz kısıtlamayı oluşturulur **IsPrimaryKey** özelliğini **doğru**.|  
  
 Aşağıdaki örnek kullanan bir XML şeması gösterir **benzersiz** benzersizlik kısıtlamasını belirtmek amacıyla öğesi.  
  
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
  
 **Benzersiz** schema öğesinde belirtir, tüm **müşteriler** bir belgedeki öğeleri örneği, değeri **CustomerID** alt öğesi benzersiz olmalıdır. Binada **DataSet**, eşleme işlemi bu şemayı okur ve aşağıdaki tabloda oluşturur:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Eşleme işlemini de UNIQUE kısıtlaması oluşturur **CustomerID** aşağıda gösterildiği gibi sütun **DataSet**. (Kolaylık sağlamak için yalnızca ilgili özellikleri gösterilir.)  
  
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
  
 İçinde **DataSet** , oluşturulduğunda, **IsPrimaryKey** özelliği ayarlanmış **False** UNIQUE kısıtlaması için. **Benzersiz** sütun özellikte gösterir **CustomerID** sütun değerleri benzersiz olmalıdır (ancak belirtildiği gibi bir null başvuru olabilir **AllowDBNull** özelliği sütun).  
  
 İçin şemayı ve isteğe bağlı ayarlarsanız **MSDATA** öznitelik değeri için **doğru**, benzersiz kısıtlamayı tablo üzerinde oluşturulur. **AllowDBNull** column özelliği ayarlanmış **False**ve **IsPrimaryKey** özellik kümesine kısıtlamasının **doğru**, böylece yapmayı **CustomerID** sütun birincil anahtar sütunu.  
  
 XML Şeması öğelerini veya öznitelikleri birleşimi benzersiz bir kısıtlama belirtebilirsiniz. Aşağıdaki örnek, belirtmek bir birleşimini gösterilmiştir **CustomerID** ve **ŞirketAdı** değerleri tümü için benzersiz olmalıdır **müşteriler** herhangi bir örneğindeki tarafından başka bir ekleme **xs:field** schema öğesinde.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Bu sonuç olarak oluşturulan sınırlamadır **DataSet**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
