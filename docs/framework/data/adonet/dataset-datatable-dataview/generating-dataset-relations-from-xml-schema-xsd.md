---
title: XML Şemasından (XSD) DataSet İlişkileri Oluşturma
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: d00f07ee3338941b7de1bb890f71cd3c2d120246
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784650"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>XML Şemasından (XSD) DataSet İlişkileri Oluşturma
Bir <xref:System.Data.DataSet>üzerinde üst-alt ilişkisi oluşturarak iki veya daha fazla sütun arasında bir ilişki oluşturursunuz. Bir XML şeması tanım dili (XSD) şeması içindeki bir **veri kümesi** ilişkisini göstermenin üç yolu vardır:  
  
- İç içe karmaşık türleri belirtin.  
  
- **Msdata: ilişki** ek açıklamasını kullanın.  
  
- **Msdata: ConstraintOnly** ek açıklaması olmadan **xs: keyref** belirtin.  
  
## <a name="nested-complex-types"></a>İç içe karmaşık türler  
 Bir şemadaki iç içe karmaşık tür tanımları, öğelerin üst-alt ilişkilerini gösterir. Aşağıdaki XML şema parçası, **OrderDetail** öğesinin **Order** öğesinin bir alt öğesi olduğunu gösterir.  
  
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
  
 XML Şeması eşleme işlemi, **veri kümesinde** , şemadaki iç içe geçmiş karmaşık türlere karşılık gelen tablolar oluşturur. Ayrıca, oluşturulan tablolar için üst **-** alt öğe olarak kullanılan ek sütunlar da oluşturur. Bu üst **-** alt öğe sütunlarının, birincil anahtar/yabancı anahtar kısıtlamalarını belirtmekle aynı olmayan ilişkiler belirttiğine unutmayın.  
  
## <a name="msdatarelationship-annotation"></a>msdata: Ilişki ek açıklaması  
 **Msdata: ilişki** ek açıklaması, şemada iç içe olmayan öğeler arasında üst-alt ilişkileri açıkça belirtmenize olanak tanır. Aşağıdaki örnek **ilişki** öğesinin yapısını gösterir.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 **Msdata: ilişki** ek açıklaması, üst-alt ilişkisine dahil olan öğeleri ve ayrıca, ilişkili **ParentKey** ve **ChildKey** öğelerini ve özniteliklerini belirler. Eşleme işlemi bu bilgileri **veri kümesinde** tablolar oluşturmak ve bu tablolar arasında birincil anahtar/yabancı anahtar ilişkisi oluşturmak için kullanır.  
  
 Örneğin, aşağıdaki şema parçası aynı düzeydeki **Order** ve **OrderDetail** öğelerini belirtir (iç içe değil). Şema, bu iki öğe arasındaki üst-alt ilişkiyi belirten bir **msdata: ilişki** ek açıklaması belirtir. Bu durumda, **msdata: ilişki** ek açıklaması kullanılarak açık bir ilişki belirtilmesi gerekir.  
  
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
  
 Eşleme işlemi **ilişki** öğesini, **Düzen** tablosundaki **OrderNumber** sütunu ve **veri kümesindeki** **OrderDetail** tablosundaki **OrderNo** sütunu arasında bir üst-alt ilişki oluşturmak için kullanır. Eşleme işlemi yalnızca ilişkiyi belirtir; ilişkisel veritabanlarındaki birincil anahtar/yabancı anahtar kısıtlamaları gibi, bu sütunlardaki değerlerde otomatik olarak herhangi bir kısıtlama belirtmez.  
  
### <a name="in-this-section"></a>Bu Bölümde  
 [İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme](map-implicit-relations-between-nested-schema-elements.md)  
 XML şemasında iç içe öğeler ile karşılaşıldığında bir **veri kümesinde** örtük olarak oluşturulan kısıtlamaları ve ilişkileri açıklar.  
  
 [İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme](map-relations-specified-for-nested-elements.md)  
 XML şemasında iç içe geçmiş öğeler için bir **veri kümesindeki** ilişkilerin açıkça nasıl ayarlanacağını açıklar.  
  
 [İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme](specify-relations-between-elements-with-no-nesting.md)  
 Bir **veri kümesinde** iç Içe olmayan xml şema öğeleri arasındaki ilişkilerin nasıl oluşturulacağını açıklar.  
  
### <a name="related-sections"></a>İlgili Bölümler  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML şeması tanım dili (XSD) şemasından oluşturulan bir **veri kümesinin** ilişkisel yapısını veya şemasını açıklar.  
  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir **veri kümesinde**benzersiz ve yabancı anahtar kısıtlamaları oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
