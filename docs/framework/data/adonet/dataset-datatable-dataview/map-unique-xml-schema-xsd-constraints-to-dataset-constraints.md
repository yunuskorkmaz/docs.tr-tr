---
title: Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 650cd6b8b8149529f115f22a11d19178fbd6d302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785380"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
Bir XML Şeması Tanım Dili (XSD) şemaya içinde **benzersiz** öğe, öğe veya öznitelik benzersizlik kısıtlamasını belirtir. Bir XML şeması bir ilişkisel şemasına çevirme sürecinde, benzersiz bir kısıtlamaya bir öğe veya öznitelik XML şemasında belirtilen UNIQUE kısıtlaması eşlenir <xref:System.Data.DataTable> karşılık gelen <xref:System.Data.DataSet> , oluşturulur.  
  
 Aşağıdaki tabloda ana hatlarını **msdata** belirleyebilirsiniz öznitelikleri **benzersiz** öğesi.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Bu öznitelik belirtilmezse, değeri kısıtlama adı kullanılır. Aksi takdirde, **adı** özniteliği kısıtlama adı değerini sağlar.|  
|**msdata:PrimaryKey**|Varsa `PrimaryKey="true"` bulunan **benzersiz** öğesi benzersiz kısıtlama ile oluşturulur **IsPrimaryKey** özelliğini **true**.|  
  
 Kullanan bir XML Şeması aşağıdaki örnekte **benzersiz** benzersizlik kısıtlamasını belirtmek için öğesi.  
  
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
  
 **Benzersiz** şema öğesi belirtir, tüm **müşteriler** bir belgedeki öğeler örneği, değerini **CustomerID** alt öğesi benzersiz olmalıdır. Binada **veri kümesi**, eşleme işlemi bu şemayı okur ve aşağıdaki tabloda oluşturur:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Eşleme işlemi aynı zamanda benzersiz kısıtlama oluşturur **CustomerID** sütun, aşağıda gösterildiği gibi **veri kümesi**. (Kolaylık olması için yalnızca ilgili özellikleri gösterilmektedir.)  
  
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
  
 İçinde **veri kümesi** , oluşturulduğunda, **IsPrimaryKey** özelliği **False** benzersiz kısıtlama için. **Benzersiz** özelliğini gösterir **CustomerID** sütun değerleri benzersiz olmalıdır (ancak bunlar tarafından belirtilen bir null başvuru olabilir **AllowDBNull** Özellik sütununun).  
  
 Şemayı değiştirmek ve isteğe bağlı **MSDATA** öznitelik değerine **True**, benzersiz kısıtlamayı tablo üzerinde oluşturulur. **AllowDBNull** column özelliği ayarlandığında **False**ve **IsPrimaryKey** özellik kümesine kısıtlamasının **True**, bu nedenle yapmayı **CustomerID** sütun birincil anahtar sütunu.  
  
 XML şemasında öğeler veya öznitelikleri birleşimi benzersiz kısıtlama belirtebilirsiniz. Aşağıdaki örnek bir birleşimi belirtme yapmayı gösteren **CustomerID** ve **CompanyName** değerleri tüm benzersiz olmalıdır **müşteriler** herhangi bir örneğindeki tarafından eklemeden **xs:field** şema öğesi.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Bu sonuç olarak oluşturulan sınırlamadır **veri kümesi**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
