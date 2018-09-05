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
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="9dd7f-102">Kesin türü belirtilmiş DataSets oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dd7f-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="9dd7f-103">XML şemasından XML şeması tanım dili ile (XSD) standart uyumlu göz önünde bulundurulduğunda, türü kesin belirlenmiş oluşturabileceğiniz <xref:System.Data.DataSet> ile sağlanan XSD.exe'nin aracını kullanarak [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9dd7f-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="9dd7f-104">(Bir xsd veritabanı tabloları oluşturmak için bkz <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio'da veri kümeleriyle çalışma](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="9dd7f-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
 <span data-ttu-id="9dd7f-105">Aşağıdaki kod oluşturma sözdizimi gösterir bir **veri kümesi** bu aracı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="9dd7f-106">Bu sözdizimi `/d` yönergesi oluşturmak için aracı söyleyen bir **veri kümesi**ve `/l:` Aracı (örneğin, C# veya Visual Basic .NET) kullanmak için hangi dilde söyler.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="9dd7f-107">İsteğe bağlı `/eld` yönergesi belirtir, kullanabileceğiniz [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] sorgulamanın yapılacağı oluşturulan **veri kümesi.**</span><span class="sxs-lookup"><span data-stu-id="9dd7f-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="9dd7f-108">Bu seçenek kullanılır, `/d` seçeneği de belirtildiğinde.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="9dd7f-109">Daha fazla bilgi için [yazılan veri kümelerini sorgulama](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="9dd7f-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="9dd7f-110">İsteğe bağlı `/n:` yönergesi ayrıca bir ad alanı oluşturmak için aracı söyler **veri kümesi** adlı **XSDSchema.Namespace**.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="9dd7f-111">Komut çıktısı, derlenmiş ve bir ADO.NET uygulamasında kullanılan XSDSchemaFileName.cs ' dir.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="9dd7f-112">Oluşturulan kod, bir kitaplık veya bir modül derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="9dd7f-113">Aşağıdaki kodu kullanarak C# Derleyici (csc.exe) kitaplık olarak oluşturulan kodu derlemek için sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="9dd7f-114">`/t:` Yönergesi söyleyen bir kitaplığa derlemek için araç ve `/r:` yönergeleri derlemek için rcxdtı.dll bağımlı kitaplıkları belirtin.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="9dd7f-115">Derleyiciye ADO.NET uygulamayla derlenirken geçirilebilir XSDSchemaFileName.dll, komut çıktısı olan `/r:` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="9dd7f-116">Aşağıdaki kod, xsd.exe'nin için bir ADO.NET uygulamasında geçirilen ad alanı erişmek için söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="9dd7f-117">Aşağıdaki kod örneği bir türü belirtilmiş kullanan **veri kümesi** adlı **CustomerDataSet** müşterilerin listesini yüklemeye **Northwind** veritabanı.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="9dd7f-118">Kullanarak veriler yüklendikten sonra **dolgu** yöntemi, örneğin her müşteri döngü **müşteriler** belirlenmiş kullanarak tablo **CustomersRow** ( **DataRow**) nesne.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="9dd7f-119">Bu doğrudan erişim sağlayan **CustomerID** için ile karşılık olarak sütun **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="9dd7f-120">Aşağıda bir örnek için kullanılan XML şeması vardır.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dd7f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd7f-121">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="9dd7f-122">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="9dd7f-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="9dd7f-123">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="9dd7f-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9dd7f-124">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9dd7f-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
