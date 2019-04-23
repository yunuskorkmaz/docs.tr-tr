---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 549579fca0179994191987097c12b6085ee91756
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119697"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
Bu bölümde bir bakış sunulmaktadır ilişkisel şemasını bir `DataSet` bir XML Şeması Tanım Dili (XSD) şeması belgesinden oluşturulmuştur. Genel olarak, her biri için `complexType` şema öğesi alt öğesi, bir tablo üretilir `DataSet`. Tablo yapısı, karmaşık tür tanımına göre belirlenir. Tablolar oluşturulur `DataSet` şemanın en üst düzey öğeleri için. Ancak, bir tablo yalnızca bir üst düzey için oluşturulur `complexType` öğesi olduğunda `complexType` öğesi iç içe başka içinde `complexType` öğesi, iç içe case `complexType` öğesi eşlenmiş durumda bir `DataTable` içinde `DataSet`.  
  
 World Wide Web Consortium (W3C) XSD hakkında daha fazla bilgi için bkz [XML şema bölüm 0: İlk öneri](https://www.w3.org/TR/xmlschema-0/), [XML Şeması Kısım 1: Yapıları öneri](https://www.w3.org/TR/xmlschema-1/)ve [XML şema bölümü 2: Veri türleri öneri](https://www.w3.org/TR/xmlschema-2/).  
  
 Aşağıdaki örnek, bir XML şeması gösterir. burada `customers` bir alt öğesidir `MyDataSet` olan öğenin bir **veri kümesi** öğesi.  
  
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
  
 Yukarıdaki örnekte, öğe `customers` bir karmaşık tür öğedir. Bu nedenle, karmaşık tür tanımı ayrıştırılır ve aşağıdaki tabloda eşleme işlemi oluşturur.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Tablodaki her bir sütunun veri türü, karşılık gelen öğe veya öznitelik belirtilen XML Şeması türünden türetilir.  
  
> [!NOTE]
>  Öğe `customers` basit XML şema veri türünde olduğu gibi **tamsayı**, hiçbir tablo oluşturulur. Tablolar, yalnızca karmaşık türler için üst düzey öğeleri oluşturulur.  
  
 Aşağıdaki XML şema **şema** öğeye sahip iki alt öğesi `InStateCustomers` ve `OutOfStateCustomers`.  
  
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
  
 Hem `InStateCustomers` ve `OutOfStateCustomers` alt öğeleri, karmaşık tür öğe (`customerType`). Bu nedenle, aşağıdaki iki özdeş tablolarda eşleme işlemi oluşturur `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML Şeması öğeleri açıklar bir `DataSet`.  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Tablo sütunlarını arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğeleri açıklar bir `DataSet`.  
  
 [XML Şema Kısıtlamaları ve İlişkileri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Açıklayan nasıl ilişkileri örtük olarak kısıtlamalarını oluşturmak için XML Şeması öğeleri kullanılarak oluşturulur bir `DataSet`.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Yük ve ilişkisel yapısını ve verileri kalıcı hale açıklar bir `DataSet` XML verileri olarak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
