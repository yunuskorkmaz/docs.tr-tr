---
title: "Kesin türü belirtilmiş veri kümeleri oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 61836196d9e11d3c87c43d4faaaeff54125bf706
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="f04b3-102">Kesin türü belirtilmiş veri kümeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="f04b3-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="f04b3-103">XML şeması tanım dili ile (XSD) standart uyumlu bir XML Şeması verildiğinde, kesin türü belirtilmiş oluşturabileceğiniz <xref:System.Data.DataSet> ile sağlanan XSD.exe'nin aracını kullanarak [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f04b3-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="f04b3-104">(Bir xsd veritabanı tablolarından oluşturmak için bkz: <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio'da veri kümeleriyle çalışma](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="f04b3-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
 <span data-ttu-id="f04b3-105">Aşağıdaki kodu oluşturmak için söz dizimi görülmektedir bir **DataSet** bu aracı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f04b3-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="f04b3-106">Bu sözdiziminde `/d` yönergesi oluşturmak için aracını söyleyen bir **DataSet**ve `/l:` aracına (örneğin, C# veya Visual Basic .NET) kullanmak için hangi dilde söyler.</span><span class="sxs-lookup"><span data-stu-id="f04b3-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="f04b3-107">İsteğe bağlı `/eld` yönergesi belirtir, kullanabileceğiniz [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] oluşturulan sorgusu için **veri kümesi.**</span><span class="sxs-lookup"><span data-stu-id="f04b3-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="f04b3-108">Bu seçenek kullanılır olduğunda `/d` seçeneği da belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="f04b3-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="f04b3-109">Daha fazla bilgi için bkz: [yazılan veri kümeleri sorgulama](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="f04b3-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="f04b3-110">İsteğe bağlı `/n:` yönergesi de için bir ad alanı oluşturmak için aracını söyler **DataSet** adlı **XSDSchema.Namespace**.</span><span class="sxs-lookup"><span data-stu-id="f04b3-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="f04b3-111">Komutunun çıktısını derlenmiş ve ADO.NET uygulamada kullanılan XSDSchemaFileName.cs ' dir.</span><span class="sxs-lookup"><span data-stu-id="f04b3-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="f04b3-112">Oluşturulan kod, bir kitaplık veya bir modül olarak derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="f04b3-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="f04b3-113">Aşağıdaki kod, C# Derleyici (csc.exe) kullanarak bir kitaplığı oluşturulan kod derleme sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f04b3-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="f04b3-114">`/t:` Yönergesi söyleyen bir kitaplığa derlemek için araç ve `/r:` yönergeleri derlemek için gereken bağımlı kitaplığı belirtin.</span><span class="sxs-lookup"><span data-stu-id="f04b3-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="f04b3-115">Komutunun çıktısını derleyiciye ADO.NET uygulamayla derlerken geçirilen XSDSchemaFileName.dll olan `/r:` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="f04b3-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="f04b3-116">Aşağıdaki kod XSD.exe'nin için bir ADO.NET uygulamada geçirilen ad alanı erişmek için söz dizimi görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="f04b3-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="f04b3-117">Aşağıdaki kod örneğinde yazılmış kullanan **DataSet** adlı **CustomerDataSet** müşterilerden yüklenmesi **Northwind** veritabanı.</span><span class="sxs-lookup"><span data-stu-id="f04b3-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="f04b3-118">Veriler kullanarak yüklendikten sonra **doldurun** yöntemi, örneğin her müşteri döngü **müşteriler** yazılı kullanarak tablo **CustomersRow** ( **DataRow**) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f04b3-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="f04b3-119">Bu doğrudan erişim sağlayan **CustomerID** için ile aygıtlardır sütun **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="f04b3-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="f04b3-120">Aşağıdaki örnek için kullanılan XML Şeması ' dir.</span><span class="sxs-lookup"><span data-stu-id="f04b3-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f04b3-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f04b3-121">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="f04b3-122">Yazılan veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="f04b3-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="f04b3-123">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="f04b3-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f04b3-124">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f04b3-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
