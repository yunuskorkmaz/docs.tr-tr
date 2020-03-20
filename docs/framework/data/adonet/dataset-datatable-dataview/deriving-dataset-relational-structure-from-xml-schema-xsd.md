---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151175"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
Bu bölümde, bir XML Şema tanım `DataSet` dili (XSD) şema belgesinden bir ilişkin şema nasıl oluşturulmuş bir genel bakış sağlar. Genel olarak, `complexType` şema öğesinin her alt öğesi için, `DataSet`bir tablo oluşturulur. Tablo yapısı karmaşık türün tanımına göre belirlenir. Tablolar şemada `DataSet` üst düzey öğeler için oluşturulur. Ancak, bir tablo yalnızca bir üst `complexType` düzey `complexType` öğe için, öğe `complexType` başka bir öğenin `complexType` içine iç içe geçtiğinde `DataTable` oluşturulur `DataSet`ve bu durumda iç içe olan öğe bir öğenin içinde eşlenir.  
  
 XSD hakkında daha fazla bilgi için, World Wide Web Konsorsiyumu (W3C) [XML Şema Bölüm 0: Primer Önerisi,](https://www.w3.org/TR/xmlschema-0/) [XML Şema Bölüm 1: Yapılar Önerisi](https://www.w3.org/TR/xmlschema-1/)ve [XML Şema Bölüm 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/)bölümüne bakın.  
  
 Aşağıdaki örnek, bir **DataSet** öğesi `customers` olan `MyDataSet` öğenin alt öğesi nin nerede olduğunu bir XML Şeması gösterir.  
  
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
  
 Önceki örnekte, öğe `customers` karmaşık bir tür öğesidir. Bu nedenle, karmaşık tür tanımı ayrıştırılır ve eşleme işlemi aşağıdaki tabloyu oluşturur.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Tablodaki her sütunun veri türü, belirtilen ilgili öğenin veya özniteliğin XML Şema türünden türetilmiştir.  
  
> [!NOTE]
> Eleman `customers` **tamsayı**gibi basit bir XML Şema veri türüne aitse, tablo oluşturulmaz. Tablolar yalnızca karmaşık türleri olan üst düzey öğeler için oluşturulur.  
  
 Aşağıdaki XML Şeması'nda **Şema** öğesiiki öğe li `InStateCustomers` ve `OutOfStateCustomers`.  
  
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
  
 Hem `InStateCustomers` alt `OutOfStateCustomers` öğeler hem de alt`customerType`öğeler karmaşık tür elemanlarıdır ( ). Bu nedenle, eşleme işlemi aşağıdaki iki `DataSet`özdeş tablolar oluşturur.  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir 'de benzersiz ve yabancı anahtar kısıtlamaları oluşturmak için `DataSet`kullanılan XML Şema öğelerini açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)  
 Tablo sütunları arasında ilişki oluşturmak için kullanılan XML `DataSet`Şema öğelerini açıklar.  
  
 [XML Şema Kısıtlamaları ve İlişkileri](xml-schema-constraints-and-relationships.md)  
 Bir 'de kısıtlamalar oluşturmak için XML Şema öğelerini kullanırken ilişkilerin nasıl örtülü olarak oluşturulduğunu `DataSet`açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 XML `DataSet` verisi olarak ilişkisel yapının ve verilerin nasıl yüklenir ve devam edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
