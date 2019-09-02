---
title: XML Web Hizmetinden DataSet Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 962163b51507647fd975815c214891a6d692e66c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203951"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="44c0e-102">XML Web Hizmetinden DataSet Kullanma</span><span class="sxs-lookup"><span data-stu-id="44c0e-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="44c0e-103">, <xref:System.Data.DataSet> Internet üzerinden veri aktarımını kolaylaştırmak için kısmen bağlantısız bir tasarıma göre tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="44c0e-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="44c0e-104">Veri kümesi, **veri KÜMESININ** içeriğini bir XML Web hizmetinden bir istemciye ve geriye doğru akışa almak için gereken ek bir kodlama olmadan XML Web hizmetlerinden bir giriş veya çıkış olarak belirtime için "serileştirilebilir" olur.</span><span class="sxs-lookup"><span data-stu-id="44c0e-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="44c0e-105">**Veri kümesi** örtük olarak, DiffGram biçimi KULLANıLARAK bir XML akışına dönüştürülür, ağ üzerinden gönderilir ve ardından XML akışından alma ucunda bir **veri kümesi** olarak yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="44c0e-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="44c0e-106">Bu, XML Web hizmetlerini kullanarak ilişkisel verileri iletmek ve döndürmek için çok basit ve esnek bir yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="44c0e-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="44c0e-107">DiffGram biçimi hakkında daha fazla bilgi için bkz. [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="44c0e-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="44c0e-108">Aşağıdaki örnek, ilişkisel verileri (değiştirilen veriler dahil) taşımak için **veri kümesini** kullanan bir XML Web hizmeti ve istemcisinin nasıl oluşturulacağını gösterir ve tüm güncelleştirmeleri özgün veri kaynağına geri çözümler.</span><span class="sxs-lookup"><span data-stu-id="44c0e-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44c0e-109">Bir XML Web hizmeti oluştururken her zaman güvenlik etkilerini düşünmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="44c0e-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="44c0e-110">Bir XML Web hizmetinin güvenliğini sağlama hakkında bilgi için bkz. [ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin güvenliğini sağlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="44c0e-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="44c0e-111">Bir veri kümesini döndüren ve tüketen bir XML Web hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="44c0e-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1. <span data-ttu-id="44c0e-112">XML Web hizmetini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44c0e-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="44c0e-113">Örnekte, verileri döndüren bir XML Web hizmeti oluşturulur ve bu durumda **Northwind** veritabanındaki müşterilerin bir listesi bulunur ve XML Web hizmeti 'nin özgün veri kaynağına geri çözümlenen veriler için güncelleştirmeler Içeren bir **veri kümesi** alır.</span><span class="sxs-lookup"><span data-stu-id="44c0e-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="44c0e-114">XML Web hizmeti iki yöntemi kullanıma sunar: Güncelleştirmeleri veri kaynağına geri çözümlemek için müşteriler ve **UpdateCustomers**listesini döndürmek üzere **GetCustomers**.</span><span class="sxs-lookup"><span data-stu-id="44c0e-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="44c0e-115">XML Web hizmeti, Web sunucusunda DataSetSample. asmx adlı bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="44c0e-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="44c0e-116">Aşağıdaki kod, DataSetSample. asmx içeriğini özetler.</span><span class="sxs-lookup"><span data-stu-id="44c0e-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     <span data-ttu-id="44c0e-117">Tipik bir senaryoda, iyimser eşzamanlılık ihlallerini yakalamak için **UpdateCustomers** yöntemi yazılır.</span><span class="sxs-lookup"><span data-stu-id="44c0e-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="44c0e-118">Kolaylık olması için örnek bunu içermez.</span><span class="sxs-lookup"><span data-stu-id="44c0e-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="44c0e-119">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz. [Iyimser eşzamanlılık](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="44c0e-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="44c0e-120">Bir XML Web hizmeti proxy 'si oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44c0e-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="44c0e-121">XML Web hizmeti istemcilerinin, sunulan yöntemleri kullanabilmesi için bir SOAP proxy 'si gerekir.</span><span class="sxs-lookup"><span data-stu-id="44c0e-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="44c0e-122">Bu proxy 'yi sizin için Visual Studio 'Nun oluşturmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44c0e-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="44c0e-123">Visual Studio içinden mevcut bir Web hizmetine bir Web başvurusu ayarlayarak, bu adımda açıklanan tüm davranışlar saydam bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="44c0e-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="44c0e-124">Proxy sınıfını kendiniz oluşturmak istiyorsanız bu tartışmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="44c0e-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="44c0e-125">Ancak çoğu durumda, istemci uygulaması için proxy sınıfı oluşturmak üzere Visual Studio kullanılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="44c0e-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="44c0e-126">Bir proxy, Web Hizmetleri Açıklama Dili Aracı kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="44c0e-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="44c0e-127">Örneğin, XML Web hizmeti URL `http://myserver/data/DataSetSample.asmx`'de açığa çıkarılacaksanız, **Webdata. dssample** ad alanı ile Visual Basic .net proxy oluşturmak için aşağıdaki gibi bir komut oluşturun ve bunu Sample. vb dosyasında depolayın.</span><span class="sxs-lookup"><span data-stu-id="44c0e-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="44c0e-128">Sample.cs dosyasında bir C# ara sunucu oluşturmak için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="44c0e-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="44c0e-129">Proxy daha sonra bir kitaplık olarak derlenebilir ve XML Web hizmeti istemcisine aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="44c0e-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="44c0e-130">Sample. vb 'de depolanan Visual Basic .NET proxy kodunu Sample. dll olarak derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="44c0e-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="44c0e-131">Sample.cs içinde depolanan C# proxy kodunu Sample. dll olarak derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="44c0e-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="44c0e-132">Bir XML Web hizmeti istemcisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44c0e-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="44c0e-133">Sizin için Visual Studio 'Nun Web hizmeti proxy sınıfını oluşturmasını istiyorsanız, yalnızca istemci projesini oluşturun ve Çözüm Gezgini penceresinde, projeye sağ tıklayın, **Web başvurusu Ekle**' ye tıklayın ve Web hizmeti ' ni listeden seçin. Hizmetler (Web hizmeti geçerli çözüm içinde veya geçerli bilgisayarda yoksa, Web hizmeti uç noktasının adresini sağlamak gerekebilir.) XML Web hizmeti proxy 'sini kendiniz oluşturursanız (önceki adımda açıklandığı gibi), istemci kodunuza içeri aktarabilir ve XML Web hizmeti yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44c0e-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="44c0e-134">Aşağıdaki örnek kod, ara kitaplığı içeri aktarır, müşterilerin listesini almak için **GetCustomers** çağırır, yeni bir müşteri ekliyor ve sonra **UpdateCustomers**güncelleştirmeleriyle birlikte bir **veri kümesi** döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="44c0e-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="44c0e-135">Örnek DataSet **. GetChanges** tarafından döndürülen **veri kümesini** **UpdateCustomers** olarak geçirdiğine dikkat edin çünkü yalnızca değiştirilen satırların **UpdateCustomers**'a geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="44c0e-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="44c0e-136">**UpdateCustomers** , çözümlenen değişiklikleri ve tüm satır hata bilgilerini güncelleştirmeden birleştirmek için, daha sonra mevcut **veri kümesiyle** birleştirebilen çözümlenmiş **veri kümesini**döndürür.</span><span class="sxs-lookup"><span data-stu-id="44c0e-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="44c0e-137">Aşağıdaki kod, Web başvurusu oluşturmak için Visual Studio kullandığınızı ve **Web başvurusu Ekle** Iletişim kutusunda dssample için Web başvurusunu yeniden adlandırdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="44c0e-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     <span data-ttu-id="44c0e-138">Proxy sınıfını kendiniz oluşturmaya karar verirseniz, aşağıdaki ek adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44c0e-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="44c0e-139">Örneği derlemek için, oluşturulan ara sunucu kitaplığını (Sample. dll) ve ilgili .NET kitaplıklarını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="44c0e-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="44c0e-140">Örneğin, Client. vb dosyasında depolanan örnek Visual Basic .NET sürümünü derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="44c0e-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="44c0e-141">Client.cs dosyasında depolanan C# örneğin sürümünü derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="44c0e-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="44c0e-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44c0e-142">See also</span></span>

- [<span data-ttu-id="44c0e-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="44c0e-143">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="44c0e-144">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="44c0e-144">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="44c0e-145">DataTables</span><span class="sxs-lookup"><span data-stu-id="44c0e-145">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="44c0e-146">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="44c0e-146">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="44c0e-147">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="44c0e-147">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="44c0e-148">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="44c0e-148">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="44c0e-149">[Web Hizmetleri Açıklama Dili Aracı (wsdl. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44c0e-149">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="44c0e-150">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="44c0e-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
