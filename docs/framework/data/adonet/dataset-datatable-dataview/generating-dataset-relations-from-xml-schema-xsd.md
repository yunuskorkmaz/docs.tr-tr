---
title: "DataSet ilişkileri XML Schema (XSD) oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 916b9ad24c2ae2334635760a520116b4c19df314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>DataSet ilişkileri XML Schema (XSD) oluşturma
İçinde bir <xref:System.Data.DataSet>, bir üst-alt ilişkisi oluşturarak iki veya daha fazla sütun arasında bir ilişki oluşturur. Göstermek için üç yolu bir **DataSet** ilişkisi bir XML Şeması Tanım Dili (XSD) şeması içinde:  
  
-   İç içe geçmiş karmaşık türler belirtin.  
  
-   Kullanım **msdata:Relationship** ek açıklama.  
  
-   Belirtin bir **xs:keyref** olmadan **msdata:ConstraintOnly** ek açıklama.  
  
## <a name="nested-complex-types"></a>İç içe geçmiş karmaşık türler  
 Bir şemadaki iç içe geçmiş karmaşık tür tanımları öğelerin üst-alt ilişkisi belirtin. Aşağıdaki XML Şeması parça gösterir **OrderDetail** bir alt öğesi olan **sipariş** öğesi.  
  
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
  
 XML şema eşleme işlemi tablolarda oluşturur **DataSet** , karşılık gelen şema iç içe geçmiş karmaşık türler için. Ayrıca üst öğe olarak kullanılan ek sütunlar oluşturur**-**alt sütunları oluşturulan tablolar için. Bu üst Not**-**alt sütunları birincil anahtarı/yabancı anahtar kısıtlamaları belirtme aynı olmayan ilişkiler belirtin.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship ek açıklaması  
 **Msdata:Relationship** ek açıklama açıkça şemadaki değil iç içe öğeler arasındaki üst-alt ilişkileri belirtmenize olanak verir. Aşağıdaki örnek, yapısını gösterir **ilişki** öğesi.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Özniteliklerini **msdata:Relationship** ek açıklama ilgili olarak üst-alt ilişkisinde, de öğeleri tanımlamak **parentkey** ve **childkey** öğeleri ve özniteliklerinin ilişkide bulunan. Eşleme işlemini, tablolar oluşturmak için bu bilgileri kullanır. **DataSet** ve bu tablolar arasındaki birincil anahtarı/yabancı anahtar ilişkisi oluşturun.  
  
 Örneğin, aşağıdaki şema parça belirtir **sipariş** ve **OrderDetail** öğeleri aynı düzeyde (iç içe değil). Şema belirten bir **msdata:Relationship** ek açıklama bu iki öğenin üst-alt ilişkisi belirtir. Bu durumda, açık bir ilişkisi kullanılarak belirtilmelidir **msdata:Relationship** ek açıklama.  
  
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
  
 Eşleme işlemini kullanan **ilişki** öğesi bir üst-alt ilişkisi oluşturmak için **OrderNumber** sütununda **sipariş** tablo ve **OrderNo** sütununda **OrderDetail** tablosundaki **DataSet**. Eşleme işlemini yalnızca ilişki belirtir; birincil anahtar/yabancı anahtar kısıtlamaları ilişkisel veritabanları gibi otomatik olarak değerlerinde kısıtlamalar bu sütunlarda belirtmiyor.  
  
### <a name="in-this-section"></a>Bu Bölümde  
 [İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Kısıtlamalar ve örtük olarak oluşturulmuş ilişkileri açıklar bir **DataSet** zaman iç içe öğelerin karşılaştı XML şeması.  
  
 [İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Açıkça ilişkileri nasıl ayarlanacağını açıklar bir **DataSet** XML Şeması iç içe geçmiş öğe.  
  
 [İç İçe Yerleştirme İçermeyen Öğeler Arasındaki İlişkileri Belirtme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 İlişkilerine oluşturmayı açıklar bir **DataSet** değil iç içe XML şema öğeleri arasında.  
  
### <a name="related-sections"></a>İlgili Bölümler  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 İlişkisel yapısı veya şema açıklayan bir **veri kümesi** XML Şeması Tanım Dili (XSD) şemadan oluşturulur.  
  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML şema öğeleri açıklayan bir **DataSet**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
