---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 878e39af575328fb0abba096c327d36203a52231
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164811"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme

Bu bölüm bir `DataSet` XML şeması tanım dili (xsd) şema belgesinden bir öğesinin ilişkisel şemasının nasıl oluşturulduğunu gösteren bir genel bakış sağlar. Genel olarak, `complexType` bir şema öğesinin her alt öğesi için içinde bir tablo oluşturulur `DataSet` . Tablo yapısı, karmaşık türün tanımına göre belirlenir. Tablolar, `DataSet` şemadaki en üst düzey öğelerde oluşturulur. Ancak, bir tablo, `complexType` öğe başka bir öğenin içinde iç içe olduğunda yalnızca üst düzey öğe için oluşturulur `complexType` `complexType` , bu durumda iç içe `complexType` öğe içinde bir ile eşlenir `DataTable` `DataSet` .  
  
 XSD hakkında daha fazla bilgi için, bkz. World Wide Web Konsorsiyumu (W3C) [XML Şeması bölümü 0: öncü öneri](https://www.w3.org/TR/xmlschema-0/), [XML şeması Bölüm 1: yapılar önerisi](https://www.w3.org/TR/xmlschema-1/)ve [XML şeması Bölüm 2: veri türleri önerisi](https://www.w3.org/TR/xmlschema-2/).  
  
 Aşağıdaki örnek, `customers` `MyDataSet` bir **veri kümesi** öğesi olan öğesinin alt öğesi olan bir XML şemasını gösterir.  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Önceki örnekte, öğesi `customers` karmaşık bir tür öğesidir. Bu nedenle, karmaşık tür tanımı ayrıştırılır ve eşleme işlemi aşağıdaki tabloyu oluşturur.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Tablodaki her sütunun veri türü, karşılık gelen öğenin veya özniteliğin XML şema türünden türetilir.  
  
> [!NOTE]
> Öğesi tamsayı gibi `customers` Basit BIR XML şeması veri türünde ise hiçbir tablo oluşturulmaz **integer**. Tablolar yalnızca karmaşık türler olan en üst düzey öğeler için oluşturulur.  
  
 Aşağıdaki XML şemasında, **şema** öğesi iki öğe alt öğesine sahiptir `InStateCustomers` ve `OutOfStateCustomers` .  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Hem `InStateCustomers` hem de `OutOfStateCustomers` alt öğeleri karmaşık tür öğeleridir ( `customerType` ). Bu nedenle, eşleme işlemi içinde aşağıdaki iki özdeş tabloyu üretir `DataSet` .  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir içinde benzersiz ve yabancı anahtar kısıtlamaları oluşturmak için kullanılan XML şema öğelerini açıklar `DataSet` .  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)  
 İçindeki tablo sütunları arasında ilişki oluşturmak için kullanılan XML şema öğelerini açıklar `DataSet` .  
  
 [XML Şema Kısıtlamaları ve İlişkileri](xml-schema-constraints-and-relationships.md)  
 Bir içinde kısıtlamalar oluşturmak için XML şema öğeleri kullanıldığında ilişkilerin örtük olarak nasıl oluşturulduğunu açıklar `DataSet` .  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 Bir as XML verilerinde ilişkisel yapının ve verilerin nasıl yükleneceğini ve kalıcı yapılacağını açıklar `DataSet` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
