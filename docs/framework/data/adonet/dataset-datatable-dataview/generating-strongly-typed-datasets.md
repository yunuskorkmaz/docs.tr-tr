---
title: Kesin Türü Belirtilmiş DataSets Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 1c65389c8c5664f86f3f0c04829a2422908d72d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202298"
---
# <a name="generating-strongly-typed-datasets"></a>Kesin Türü Belirtilmiş DataSets Oluşturma

XML şeması tanım dili (XSD) standardına uygun bir XML şeması verildiğinde, <xref:System.Data.DataSet> Windows yazılım geliştirme seti (SDK) ile sağlanan XSD.exe aracını kullanarak kesin bir tür oluşturabilirsiniz.  
  
 (Veritabanı tablolarından bir xsd oluşturmak için, bkz <xref:System.Data.DataSet.WriteXmlSchema%2A> . veya [Visual Studio 'Da veri kümeleri ile çalışma](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 Aşağıdaki kod, bu aracı kullanarak bir **veri kümesi** oluşturmak için söz dizimini gösterir.  
  
```console  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Bu sözdiziminde, `/d` yönerge araca bir **veri kümesi**oluşturmasını söyler ve `/l:` araca hangi dilin kullanılacağını söyler (örneğin, C# veya Visual Basic .net). İsteğe bağlı `/eld` yönerge, oluşturulan **veri kümesinde** sorgulama yapmak için LINQ to DataSet kullanacağınızı belirtir. Seçenek de belirtildiğinde bu seçenek kullanılır `/d` . Daha fazla bilgi için bkz. [türü belirtilmiş veri kümelerini sorgulama](../querying-typed-datasets.md). İsteğe bağlı `/n:` yönerge, araca **XSDSchema. Namespace**adlı **veri kümesi** için de bir ad alanı oluşturmasını söyler. Komutun çıktısı, bir ADO.NET uygulamasında derlenebilecek ve kullanılabilecek olan XSDSchemaFileName.cs 'dir. Oluşturulan kod bir kitaplık veya modül olarak derlenebilir.  
  
 Aşağıdaki kod, oluşturulan kodu C# derleyicisini kullanarak bir kitaplık olarak derlemek için sözdizimini gösterir (csc.exe).  
  
```console  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:`Yönergesi, araca bir kitaplığa derlemeyi söyler ve `/r:` yönergeler derlemek için gereken bağımlı kitaplıkları belirler. Komutun çıktısı, yönergeyle bir ADO.NET uygulaması derlenirken derleyiciye geçirilebilen XSDSchemaFileName.dll `/r:` .  
  
 Aşağıdaki kod, bir ADO.NET uygulamasında XSD.exe geçirilen ad alanına erişim söz dizimini gösterir.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Aşağıdaki kod örneği, **Northwind** veritabanından müşterilerin bir listesini yüklemek Için **customerdataset** adlı bir türü belirtilmiş **veri kümesini** kullanır. **Fill** yöntemi kullanılarak veriler yüklendikten sonra örnek, yazılan **CustomersRow** (**DataRow**) nesnesini kullanarak **müşteriler** tablosundaki her bir müşteri için döngü gerçekleştirilir. Bu, **DataColumnCollection**yerine **MüşteriNo** sütununa doğrudan erişim sağlar.  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 Örnek için kullanılan XML şeması aşağıda verilmiştir:
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Türü Belirtilmiş DataSets](typed-datasets.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
