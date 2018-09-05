---
title: Kesin türü belirtilmiş DataSets oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 9accfb68c57384e12a59bae40ebe30a2d3e22877
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526494"
---
# <a name="generating-strongly-typed-datasets"></a>Kesin türü belirtilmiş DataSets oluşturma
XML şemasından XML şeması tanım dili ile (XSD) standart uyumlu göz önünde bulundurulduğunda, türü kesin belirlenmiş oluşturabileceğiniz <xref:System.Data.DataSet> ile sağlanan XSD.exe'nin aracını kullanarak [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 (Bir xsd veritabanı tabloları oluşturmak için bkz <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio'da veri kümeleriyle çalışma](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
 Aşağıdaki kod oluşturma sözdizimi gösterir bir **veri kümesi** bu aracı kullanarak.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Bu sözdizimi `/d` yönergesi oluşturmak için aracı söyleyen bir **veri kümesi**ve `/l:` Aracı (örneğin, C# veya Visual Basic .NET) kullanmak için hangi dilde söyler. İsteğe bağlı `/eld` yönergesi belirtir, kullanabileceğiniz [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] sorgulamanın yapılacağı oluşturulan **veri kümesi.** Bu seçenek kullanılır, `/d` seçeneği de belirtildiğinde. Daha fazla bilgi için [yazılan veri kümelerini sorgulama](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). İsteğe bağlı `/n:` yönergesi ayrıca bir ad alanı oluşturmak için aracı söyler **veri kümesi** adlı **XSDSchema.Namespace**. Komut çıktısı, derlenmiş ve bir ADO.NET uygulamasında kullanılan XSDSchemaFileName.cs ' dir. Oluşturulan kod, bir kitaplık veya bir modül derlenebilir.  
  
 Aşağıdaki kodu kullanarak C# Derleyici (csc.exe) kitaplık olarak oluşturulan kodu derlemek için sözdizimi gösterilmektedir.  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` Yönergesi söyleyen bir kitaplığa derlemek için araç ve `/r:` yönergeleri derlemek için rcxdtı.dll bağımlı kitaplıkları belirtin. Derleyiciye ADO.NET uygulamayla derlenirken geçirilebilir XSDSchemaFileName.dll, komut çıktısı olan `/r:` yönergesi.  
  
 Aşağıdaki kod, xsd.exe'nin için bir ADO.NET uygulamasında geçirilen ad alanı erişmek için söz dizimini gösterir.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Aşağıdaki kod örneği bir türü belirtilmiş kullanan **veri kümesi** adlı **CustomerDataSet** müşterilerin listesini yüklemeye **Northwind** veritabanı. Kullanarak veriler yüklendikten sonra **dolgu** yöntemi, örneğin her müşteri döngü **müşteriler** belirlenmiş kullanarak tablo **CustomersRow** ( **DataRow**) nesne. Bu doğrudan erişim sağlayan **CustomerID** için ile karşılık olarak sütun **DataColumnCollection**.  
  
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
  
 Aşağıda bir örnek için kullanılan XML şeması vardır.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
