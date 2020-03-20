---
title: XML Şemasından (XSD) DataSet İlişkileri Oluşturma
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151136"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>XML Şemasından (XSD) DataSet İlişkileri Oluşturma
Bir <xref:System.Data.DataSet>, bir üst-alt ilişkisi oluşturarak iki veya daha fazla sütun arasında bir ilişki oluşturursunuz. Bir XML Şema tanım dili (XSD) şeması içinde bir **DataSet** ilişkisini temsil etmenin üç yolu vardır:  
  
- İç içe karmaşık türleri belirtin.  
  
- **msdata:İlişki** ek açıklamasını kullanın.  
  
- Msdata olmadan bir **xs:keyref** **belirtin:ConstraintOnly** ek açıklama.  
  
## <a name="nested-complex-types"></a>İç Içe Karmaşık Türleri  
 Şemada iç içe yer alan karmaşık tür tanımları, öğelerin üst-alt ilişkilerini gösterir. Aşağıdaki XML Şema **parçası, OrderDetail'ın** **Sipariş** öğesinin alt öğesi olduğunu gösterir.  
  
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
  
 XML Şema eşleme işlemi, **DataSet'te** şemadaki iç içe geçen karmaşık türlere karşılık gelen tablolar oluşturur. Ayrıca, oluşturulan tablolar için üst**-** alt sütunolarak kullanılan ek sütunlar oluşturur. Bu üst**-** alt sütunların, birincil anahtar/yabancı anahtar kısıtlamalarını belirtmekle aynı olmayan ilişkileri belirtdiğini unutmayın.  
  
## <a name="msdatarelationship-annotation"></a>msdata:İlişki Açıklama  
 **msdata:İlişki** ek belirti, şemada iç içe geçmemiş öğeler arasındaki üst-alt ilişkilerini açıkça belirtmenize olanak tanır. Aşağıdaki örnek, **İlişki** öğesinin yapısını gösterir.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 **msdata'nın öznitelikleri:İlişki** ek açıklama, üst-alt ilişkisinde yer alan öğelerin yanı sıra **ilişkide** yer alan üst anahtar ve **alt anahtar** öğelerini ve öznitelikleritanımlar. Eşleme işlemi, Bu bilgileri **DataSet'te** tablo oluşturmak ve bu tablolar arasındaki birincil anahtar/yabancı anahtar ilişkisini oluşturmak için kullanır.  
  
 Örneğin, aşağıdaki şema parçası **Sipariş** ve **OrderDetail** öğelerini aynı düzeyde (iç içe değil) belirtir. Şema, bu iki öğe arasındaki üst-alt ilişkisini belirten bir **msdata:İlişki** ek açıklamasını belirtir. Bu durumda, **msdata:İlişki** ek açıklama kullanılarak açık bir ilişki belirtilmelidir.  
  
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
  
 Eşleme işlemi, **Sipariş** tablosundaki **OrderNumber sütunu** ile **DataSet'teki**OrderDetail tablosundaki **OrderNo** sütunu arasında üst-alt ilişki oluşturmak için **İlişki** öğesini kullanır. **OrderNo** Eşleme işlemi yalnızca ilişkiyi belirtir; bu sütunlarda değerler üzerinde herhangi bir kısıtlama otomatik olarak belirtmez, ilişkisel veritabanlarında birincil anahtar/yabancı anahtar kısıtlamaları gibi.  
  
### <a name="in-this-section"></a>Bu Bölümde  
 [İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme](map-implicit-relations-between-nested-schema-elements.md)  
 XML Schema'da iç içe geçmiş öğelerle **karşılaşıldığında, bir DataSet'te** örtülü olarak oluşturulan kısıtlamaları ve ilişkileri açıklar.  
  
 [İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme](map-relations-specified-for-nested-elements.md)  
 XML Şeması'nda iç içe geçen öğeler için bir **DataSet'teki** ilişkileri açıkça nasıl ayarlayabilirsiniz açıklar.  
  
 [İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme](specify-relations-between-elements-with-no-nesting.md)  
 İç içe geçmemiş XML Şema öğeleri arasında **Bir DataSet'te** nasıl ilişki oluşturulacak açıklanır.  
  
### <a name="related-sections"></a>İlgili Bölümler  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML Şema tanım dili (XSD) şemasından oluşturulan bir **DataSet'in** ilişkisel yapısını veya şemasını açıklar.  
  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **DataSet'te**benzersiz ve yabancı anahtar kısıtlamaları oluşturmak için kullanılan XML Şema öğelerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
