---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 98c43b6af2913b9737085d2d983b37c6da4c1724
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934465"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
Bu bölüm bir XML şeması tanım dili (xsd) şema belgesinden `DataSet` bir öğesinin ilişkisel şemasının nasıl oluşturulduğunu gösteren bir genel bakış sağlar. Genel olarak, bir şema `complexType` öğesinin her alt öğesi için `DataSet`içinde bir tablo oluşturulur. Tablo yapısı, karmaşık türün tanımına göre belirlenir. Tablolar, `DataSet` şemadaki en üst düzey öğelerde oluşturulur. Ancak, bir `complexType` tablo, `complexType` öğe başka `complexType` bir öğenin içinde iç içe olduğunda yalnızca üst düzey öğe için oluşturulur, bu durumda `DataSet`iç içe `complexType` öğe içinde bir `DataTable` ile eşlenir.  
  
 XSD hakkında daha fazla bilgi için bkz. World Wide Web Konsorsiyumu (W3C) [XML Şeması bölümü 0: Öncü öneri](https://www.w3.org/TR/xmlschema-0/) [, XML şeması Bölüm 1: Yapılar önerisi](https://www.w3.org/TR/xmlschema-1/) [ve XML şeması Bölüm 2: Veri türleri](https://www.w3.org/TR/xmlschema-2/)önerisi.  
  
 Aşağıdaki örnek, bir **veri kümesi** öğesi olan `customers` `MyDataSet` öğesinin alt öğesi olan bir XML şemasını gösterir.  
  
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
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Tablodaki her sütunun veri türü, karşılık gelen öğenin veya özniteliğin XML şema türünden türetilir.  
  
> [!NOTE]
> Öğesi `customers` **tamsayı**gibi basit bir XML şeması veri türünde ise hiçbir tablo oluşturulmaz. Tablolar yalnızca karmaşık türler olan en üst düzey öğeler için oluşturulur.  
  
 Aşağıdaki XML şemasında, **şema** öğesi iki öğe alt `InStateCustomers` öğesine sahiptir ve. `OutOfStateCustomers`  
  
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
  
 `InStateCustomers` Hem`customerType`hem de altöğelerikarmaşıktür`OutOfStateCustomers` öğeleridir (). Bu nedenle, eşleme işlemi içinde `DataSet`aşağıdaki iki özdeş tabloyu üretir.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir `DataSet`içinde benzersiz ve yabancı anahtar kısıtlamaları oluşturmak Için kullanılan xml şema öğelerini açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 İçindeki tablo sütunları arasında ilişki oluşturmak için kullanılan XML şema öğelerini açıklar `DataSet`.  
  
 [XML Şema Kısıtlamaları ve İlişkileri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Bir `DataSet`içinde kısıtlamalar oluşturmak için XML şema öğeleri kullanıldığında ilişkilerin örtük olarak nasıl oluşturulduğunu açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Bir `DataSet` as XML verilerinde ilişkisel yapının ve verilerin nasıl yükleneceğini ve kalıcı yapılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
