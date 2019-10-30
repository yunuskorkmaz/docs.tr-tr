---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: ef77030b4e847f91fea074b68e223ac622539048
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040097"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
Bu bölüm, bir `DataSet` ilişkisel şemasının bir XML şeması tanım dili (XSD) şema belgesinden nasıl oluşturulduğunu gösteren bir genel bakış sağlar. Genel olarak, bir şema öğesinin her bir `complexType` alt öğesi için `DataSet`bir tablo oluşturulur. Tablo yapısı, karmaşık türün tanımına göre belirlenir. Tablolar, şemadaki üst düzey öğeler için `DataSet` oluşturulur. Ancak, bir tablo yalnızca bir üst düzey `complexType` `complexType` `complexType` öğesi için oluşturulur. Bu durumda, iç içe yerleştirilmiş `complexType` öğesi `DataTable` içindeki bir `DataSet`eşlenir.  
  
 XSD hakkında daha fazla bilgi için, bkz. World Wide Web Konsorsiyumu (W3C) [XML Şeması bölümü 0: öncü öneri](https://www.w3.org/TR/xmlschema-0/), [XML şeması Bölüm 1: yapılar önerisi](https://www.w3.org/TR/xmlschema-1/)ve [XML şeması Bölüm 2: veri türleri önerisi](https://www.w3.org/TR/xmlschema-2/).  
  
 Aşağıdaki örnek, `customers` bir **veri kümesi** öğesi olan `MyDataSet` öğesinin alt öğesi olduğu bir XML şemasını gösterir.  
  
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
> Öğe `customers` **tamsayı**gibi basıt bir XML şeması veri türü ise hiçbir tablo oluşturulmaz. Tablolar yalnızca karmaşık türler olan en üst düzey öğeler için oluşturulur.  
  
 Aşağıdaki XML şemasında, **şema** öğesinde iki öğe alt öğesi vardır `InStateCustomers` ve `OutOfStateCustomers`.  
  
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
  
 Hem `InStateCustomers` hem de `OutOfStateCustomers` alt öğeleri karmaşık tür öğeleridir (`customerType`). Bu nedenle, eşleme işlemi `DataSet`aşağıdaki iki özdeş tabloyu üretir.  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir `DataSet`benzersiz ve yabancı anahtar kısıtlamaları oluşturmak için kullanılan XML şema öğelerini açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)  
 Bir `DataSet`tablo sütunları arasında ilişki oluşturmak için kullanılan XML şema öğelerini açıklar.  
  
 [XML Şema Kısıtlamaları ve İlişkileri](xml-schema-constraints-and-relationships.md)  
 Bir `DataSet`kısıtlamalar oluşturmak için XML şema öğeleri kullanıldığında ilişkilerin örtük olarak nasıl oluşturulduğunu açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 Bir `DataSet` ilişkisel yapının ve verilerin XML verileri olarak nasıl yükleneceğini ve kalıcı yapılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
