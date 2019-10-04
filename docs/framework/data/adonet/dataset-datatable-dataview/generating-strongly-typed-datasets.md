---
title: Kesin türü belirtilmiş veri kümeleri oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: ce7e5ad53f7aa5dad457ca1aa6ab76716086c0c3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833985"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="d407c-102">Kesin türü belirtilmiş veri kümeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d407c-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="d407c-103">XML şeması tanım dili (XSD) standardına uygun bir XML şeması verildiğinde, Windows yazılım geliştirme seti (SDK) ile sağlanan XSD. exe aracını kullanarak türü kesin belirlenmiş <xref:System.Data.DataSet> oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d407c-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="d407c-104">(Veritabanı tablolarından bir xsd oluşturmak için, bkz. <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio 'Da veri kümeleriyle çalışma](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="d407c-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="d407c-105">Aşağıdaki kod, bu aracı kullanarak bir **veri kümesi** oluşturmak için söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d407c-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="d407c-106">Bu sözdiziminde, `/d` yönergesi araca bir **veri kümesi**oluşturmasını söyler ve `/l:` araca hangi dilin kullanılacağını söyler (örneğin, C# veya Visual Basic .net).</span><span class="sxs-lookup"><span data-stu-id="d407c-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="d407c-107">İsteğe bağlı `/eld` yönergesi, oluşturulan **veri kümesinde** sorgulama yapmak için LINQ to DataSet kullanacağınızı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d407c-107">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="d407c-108">@No__t-0 seçeneği de belirtildiğinde bu seçenek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d407c-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="d407c-109">Daha fazla bilgi için bkz. [türü belirtilmiş veri kümelerini sorgulama](../querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="d407c-109">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="d407c-110">İsteğe bağlı `/n:` yönergesi, araca **XSDSchema. Namespace**adlı **veri kümesi** için de bir ad alanı oluşturmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="d407c-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="d407c-111">Komutun çıktısı, bir ADO.NET uygulamasında derlenebilecek ve kullanılabilecek olan XSDSchemaFileName.cs 'dir.</span><span class="sxs-lookup"><span data-stu-id="d407c-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="d407c-112">Oluşturulan kod bir kitaplık veya modül olarak derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="d407c-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="d407c-113">Aşağıdaki kod, C# derleyicinin (CSC. exe) kullanılarak oluşturulan kodu bir kitaplık olarak derlemek için söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d407c-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="d407c-114">@No__t-0 yönergesi, araca bir kitaplığa derlemeyi söyler ve `/r:` yönergeleri derlemek için gereken bağımlı kitaplıkları belirtir.</span><span class="sxs-lookup"><span data-stu-id="d407c-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="d407c-115">Komutun çıktısı, `/r:` yönergesi ile bir ADO.NET uygulaması derlenirken derleyiciye geçirilebilecek XSDSchemaFileName. dll ' dir.</span><span class="sxs-lookup"><span data-stu-id="d407c-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="d407c-116">Aşağıdaki kod, bir ADO.NET uygulamasında XSD. exe ' ye geçirilen ad alanına erişim söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d407c-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="d407c-117">Aşağıdaki kod örneği, **Northwind** veritabanından müşterilerin bir listesini yüklemek Için **customerdataset** adlı bir türü belirtilmiş **veri kümesini** kullanır.</span><span class="sxs-lookup"><span data-stu-id="d407c-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="d407c-118">**Fill** yöntemi kullanılarak veriler yüklendikten sonra örnek, yazılan **CustomersRow** (**DataRow**) nesnesini kullanarak **müşteriler** tablosundaki her bir müşteri için döngü gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d407c-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="d407c-119">Bu, **DataColumnCollection**yerine **MüşteriNo** sütununa doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d407c-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="d407c-120">Örnek için kullanılan XML şeması aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d407c-120">The following is the XML Schema used for the example:</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="d407c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d407c-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="d407c-122">Türü belirtilmiş veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="d407c-122">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="d407c-123">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="d407c-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d407c-124">ADO.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="d407c-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
