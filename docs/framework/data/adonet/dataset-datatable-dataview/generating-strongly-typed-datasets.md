---
title: Kesin türü belirtilmiş veri kümeleri oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 95bb536416a043fc392d0c4e94378239ae3ee37f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758035"
---
# <a name="generating-strongly-typed-datasets"></a>Kesin türü belirtilmiş veri kümeleri oluşturma
XML şeması tanım dili ile (XSD) standart uyumlu bir XML Şeması verildiğinde, kesin türü belirtilmiş oluşturabileceğiniz <xref:System.Data.DataSet> ile sağlanan XSD.exe'nin aracını kullanarak [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 (Bir xsd veritabanı tablolarından oluşturmak için bkz: <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio'da veri kümeleriyle çalışma](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
 Aşağıdaki kodu oluşturmak için söz dizimi görülmektedir bir **DataSet** bu aracı kullanarak.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Bu sözdiziminde `/d` yönergesi oluşturmak için aracını söyleyen bir **DataSet**ve `/l:` aracına (örneğin, C# veya Visual Basic .NET) kullanmak için hangi dilde söyler. İsteğe bağlı `/eld` yönergesi belirtir, kullanabileceğiniz [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] oluşturulan sorgusu için **veri kümesi.** Bu seçenek kullanılır olduğunda `/d` seçeneği da belirtilmiş. Daha fazla bilgi için bkz: [yazılan veri kümeleri sorgulama](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). İsteğe bağlı `/n:` yönergesi de için bir ad alanı oluşturmak için aracını söyler **DataSet** adlı **XSDSchema.Namespace**. Komutunun çıktısını derlenmiş ve ADO.NET uygulamada kullanılan XSDSchemaFileName.cs ' dir. Oluşturulan kod, bir kitaplık veya bir modül olarak derlenebilir.  
  
 Aşağıdaki kod, C# Derleyici (csc.exe) kullanarak bir kitaplığı oluşturulan kod derleme sözdizimi gösterilmektedir.  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` Yönergesi söyleyen bir kitaplığa derlemek için araç ve `/r:` yönergeleri derlemek için gereken bağımlı kitaplığı belirtin. Komutunun çıktısını derleyiciye ADO.NET uygulamayla derlerken geçirilen XSDSchemaFileName.dll olan `/r:` yönergesi.  
  
 Aşağıdaki kod XSD.exe'nin için bir ADO.NET uygulamada geçirilen ad alanı erişmek için söz dizimi görülmektedir.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Aşağıdaki kod örneğinde yazılmış kullanan **DataSet** adlı **CustomerDataSet** müşterilerden yüklenmesi **Northwind** veritabanı. Veriler kullanarak yüklendikten sonra **doldurun** yöntemi, örneğin her müşteri döngü **müşteriler** yazılı kullanarak tablo **CustomersRow** ( **DataRow**) nesnesi. Bu doğrudan erişim sağlayan **CustomerID** için ile aygıtlardır sütun **DataColumnCollection**.  
  
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
  
 Aşağıdaki örnek için kullanılan XML Şeması ' dir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Türü Belirtilmiş DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
