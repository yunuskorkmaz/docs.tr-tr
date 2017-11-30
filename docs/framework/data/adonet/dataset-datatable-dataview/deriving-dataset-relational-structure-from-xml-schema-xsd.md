---
title: "Türetilen DataSet ilişkisel yapısından XML Şeması (XSD)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0aae23c295401d4b9565c35d4d47c5ab913029d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Türetilen DataSet ilişkisel yapısından XML Şeması (XSD)
Bu bölüm, nasıl bir bakış sağlar ve ilişkisel şema bir `DataSet` XML Şeması Tanım Dili (XSD) şema belgesi yerleşik olarak bulunur. Genel olarak, her biri için `complexType` şema öğesinin alt öğesi, bir tablo üretilir `DataSet`. Tablo yapısı karmaşık tür tanımı tarafından belirlenir. Tabloları oluşturulan `DataSet` şemanın en üst düzey öğe. Ancak, bir tablo yalnızca bir üst düzey için oluşturulan `complexType` öğesi zaman `complexType` öğesiyle başka içe `complexType` öğesi, iç içe durumda `complexType` öğesi eşleştirilir bir `DataTable` içinde `DataSet`.  
  
 World Wide Web Konsorsiyumu (W3C) XML Şeması bölümü 0 XSD hakkında daha fazla bilgi için bkz: Primer öneri, XML Şeması Kısım 1: yapıları öneri ve XML Şeması Kısım 2: veri türleri öneri, konumunda bulunan [http:// www.w3.org/](http://www.w3.org/TR/).  
  
 Aşağıdaki örnek, bir XML şeması gösterir nerede `customers` alt öğenin `MyDataSet` olan öğenin bir **DataSet** öğesi.  
  
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
  
 Önceki örnekte, öğe `customers` bir karmaşık tür öğedir. Bu nedenle, karmaşık tür tanımı ayrıştırılır ve aşağıdaki tabloda eşleme işlemi oluşturur.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Tablodaki her sütun veri türü karşılık gelen öğe veya öznitelik belirtilen XML Şeması türünden türetilir.  
  
> [!NOTE]
>  Varsa öğe `customers` olduğu gibi basit bir XML Şeması veri türünü **tamsayı**, hiçbir tablo oluşturulur. Tabloları yalnızca karmaşık türler için üst düzey öğeleri oluşturulur.  
  
 Aşağıdaki XML şemasında **şema** öğeye sahip iki alt öğesi `InStateCustomers` ve `OutOfStateCustomers`.  
  
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
  
 Hem `InStateCustomers` ve `OutOfStateCustomers` alt öğeleri olan karmaşık tür öğeleri (`customerType`). Bu nedenle, aşağıdaki iki özdeş Tablo eşleme işlemi oluşturur `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri kümesi sınırlamaları için eşleme XML Şeması (XSD) kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML şema öğeleri açıklayan bir `DataSet`.  
  
 [DataSet ilişkileri XML Schema (XSD) oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Tablo sütunları arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğelerini açıklar bir `DataSet`.  
  
 [XML şema kısıtlamaları ve ilişkileri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Nasıl ilişkileri örtük olarak XML şema öğeleri kısıtlamalar oluşturmak için kullanırken oluşturulduğunu açıklayan bir `DataSet`.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bir veri kümesini XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Yük ve ilişkisel yapısı ve verilerde kalıcı açıklar bir `DataSet` XML verileri olarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
