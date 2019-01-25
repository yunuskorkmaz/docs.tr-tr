---
title: XML şemasından (XSD) DataSet ilişkileri oluşturma
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: b74c992c4569512a8692b70663002fd609d3501e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546146"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>XML şemasından (XSD) DataSet ilişkileri oluşturma
İçinde bir <xref:System.Data.DataSet>, bir üst-alt ilişkisi oluşturarak iki veya daha fazla sütunu arasında bir ilişki oluşturur. Göstermek için üç yol vardır bir **veri kümesi** ilişkisi içinde bir XML Şeması Tanım Dili (XSD) şeması:  
  
-   Karmaşık iç içe geçmiş türler belirtin.  
  
-   Kullanım **msdata:Relationship** ek açıklama.  
  
-   Belirtin bir **xs:keyref** olmadan **msdata:ConstraintOnly** ek açıklama.  
  
## <a name="nested-complex-types"></a>Karmaşık iç içe geçmiş türler  
 İç içe geçmiş bir karmaşık tür tanımlarını bir şemadaki öğelerin üst-alt ilişkileri gösterir. Aşağıdaki XML Şeması parçası gösteren **OrderDetail** bir alt öğesidir **sipariş** öğesi.  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 XML Şeması eşleme işlemi tablolarında oluşturur **veri kümesi** karşılık gelen şema karmaşık iç içe geçmiş türleri için. Üst öğe olarak kullanılan ek sütunlar da oluşturur**-** oluşturulan tablolar için alt sütunlar. Bu üst Not**-** alt sütunlar, birincil anahtar/yabancı anahtar kısıtlamalarını belirtmekle aynı değil ilişkileri belirtin.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship ek açıklaması  
 **Msdata:Relationship** ek açıklama, iç içe yerleştirilmiş şema öğeleri arasında üst-alt ilişkileri açıkça belirtmenize olanak sağlar. Aşağıdaki örnek, yapısını gösterir. **ilişki** öğesi.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Özniteliklerini **msdata:Relationship** ek açıklamayı tanımlamak ilgili olarak üst-alt ilişkisinde, de öğeleri **parentkey** ve **childkey** öğeler ve öznitelikler ilişkide bulunan. Eşleme işlemi içinde tablolar oluşturmak için bu bilgileri kullanır. **veri kümesi** ve bu tablolar arasındaki birincil anahtarı/yabancı anahtar ilişkisi oluşturmak için.  
  
 Örneğin, aşağıdaki şema parçası belirtir **sipariş** ve **OrderDetail** öğeleri aynı düzeyde (iç içe olmayan). Şemayı belirtir bir **msdata:Relationship** bu iki öğe arasındaki üst-alt ilişkisi belirten açıklama. Bu durumda, açık bir ilişkisi kullanılarak belirtilmelidir **msdata:Relationship** ek açıklama.  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 Eşleme işlemi kullanır **ilişki** arasında üst-alt ilişkisi oluşturmak için öğe **OrderNumber** sütununda **sipariş** tablo ve **OrderNo** sütununda **OrderDetail** tablosundaki **veri kümesi**. Eşleme işlemi yalnızca ilişkiyi belirtir. birincil anahtarı/yabancı anahtar kısıtlamalarını ilişkisel veritabanları gibi otomatik olarak kısıtlamalardan değerleri bu sütunlarda belirtmiyor.  
  
### <a name="in-this-section"></a>Bu Bölümde  
 [İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Örtük olarak oluşturulan ilişkileri ve kısıtlamaları açıklar bir **veri kümesi** , iç içe öğelerin karşılaştı içinde XML şeması.  
  
 [İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Açıkça ilişkileri kümesinde açıklar bir **veri kümesi** XML Şeması iç içe geçmiş öğe.  
  
 [İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 İlişkiler oluşturmayı açıklar bir **veri kümesi** iç içe yerleştirilmiş bir XML Şeması öğeleri arasında.  
  
### <a name="related-sections"></a>İlgili Bölümler  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 İlişkisel yapısını veya şema biri açıklar bir **veri kümesi** XML Şeması Tanım Dili (XSD) şemaya oluşturulur.  
  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
