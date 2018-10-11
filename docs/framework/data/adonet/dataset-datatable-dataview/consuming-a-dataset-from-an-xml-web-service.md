---
title: Bir XML Web hizmetinden DataSet kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 7e43d423109ea39a725a4bfa8b9d2b22a25cfb5c
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087342"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="ce0af-102">Bir XML Web hizmetinden DataSet kullanma</span><span class="sxs-lookup"><span data-stu-id="ce0af-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="ce0af-103"><xref:System.Data.DataSet> Kısmen Internet üzerinden veri uygun taşıma kolaylaştırmak için bağlantısı kesik bir tasarım ile için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce0af-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="ce0af-104">**Veri kümesi** girdi olarak belirlenebilir veya ek kodlamaya gerek kalmadan, XML Web Hizmetleri çıktısını gerekli içeriğini akışını sağlamak için "seri hale getirilebilir" olan **veri kümesi** bir XML Web hizmeti bir istemci ve arka.</span><span class="sxs-lookup"><span data-stu-id="ce0af-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="ce0af-105">**Veri kümesi** örtük olarak biçimini kullanarak bir XML akışı dönüştürülür, ağ üzerinden gönderilen ve ardından XML Akışı'ndan reconstructed bir **veri kümesi** alan uçta.</span><span class="sxs-lookup"><span data-stu-id="ce0af-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="ce0af-106">Bu, basit ve esnek bir yöntem iletme ve XML Web Hizmetleri kullanarak ilişkisel verileri döndürmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce0af-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="ce0af-107">Biçimini hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="ce0af-107">For more information about the DiffGram format, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>  
  
 <span data-ttu-id="ce0af-108">Aşağıdaki örnek, bir XML Web hizmeti ve Kullan istemci oluşturma işlemi gösterilmektedir **veri kümesi** (değiştirilen veriler dahil) ilişkisel verilerin taşınması ve güncelleştirmelerden özgün veri kaynağına geri çözmek için.</span><span class="sxs-lookup"><span data-stu-id="ce0af-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce0af-109">Biz, her zaman güvenlikle ilgili etkileri XML Web hizmeti oluştururken düşünmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="ce0af-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="ce0af-110">XML Web hizmeti güvenli hale getirme hakkında daha fazla bilgi için bkz: [güvenli hale getirme XML Web Hizmetleri oluşturulan kullanarak ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span><span class="sxs-lookup"><span data-stu-id="ce0af-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="ce0af-111">Bir veri kümesini kullanan ve döndüren bir XML Web hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ce0af-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1.  <span data-ttu-id="ce0af-112">XML Web hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ce0af-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="ce0af-113">Örnekte, veri, bu durumda, müşterilerin listesini döndüren bir XML Web hizmeti oluşturulur **Northwind** veritabanı ve alan bir **veri kümesi** veri güncelleştirmeleri, XML Web hizmeti Özgün veri kaynağına çözümler.</span><span class="sxs-lookup"><span data-stu-id="ce0af-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="ce0af-114">XML Web hizmeti iki yöntem sunar: **GetCustomers**, müşteriler, listesini döndürmek için ve **UpdateCustomers**, güncelleştirmeleri veri kaynağına geri çözümlenecek.</span><span class="sxs-lookup"><span data-stu-id="ce0af-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="ce0af-115">XML Web hizmeti, Web sunucusunda DataSetSample.asmx adlı bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="ce0af-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="ce0af-116">Aşağıdaki kod DataSetSample.asmx içeriğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce0af-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="ce0af-117">Tipik bir senaryoda **UpdateCustomers** yöntemi iyimser eşzamanlılık ihlalleri yakalayıp yakalamayacağınıza karar yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce0af-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="ce0af-118">Kolaylık olması için bu örnek içermez.</span><span class="sxs-lookup"><span data-stu-id="ce0af-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="ce0af-119">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="ce0af-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span></span>  
  
2.  <span data-ttu-id="ce0af-120">Bir XML Web hizmeti proxy oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ce0af-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="ce0af-121">XML Web hizmeti istemcilerine kullanıma sunulan yöntemleri kullanmak için bir SOAP proxy gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ce0af-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="ce0af-122">Visual Studio sizin için bu proxy oluşturmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce0af-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="ce0af-123">Bir mevcut Web hizmetinden Visual Studio'dan bir Web başvurusu ayarlayarak bu adımda açıklandığı gibi davranış şeffaf bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ce0af-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="ce0af-124">Proxy sınıfı kendiniz oluşturmak istiyorsanız, bu tartışma ile devam edin.</span><span class="sxs-lookup"><span data-stu-id="ce0af-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="ce0af-125">Çoğu durumda, ancak istemci uygulamanın proxy sınıfı oluşturmak için Visual Studio kullanarak yeterli olur.</span><span class="sxs-lookup"><span data-stu-id="ce0af-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="ce0af-126">Bir proxy Web Hizmetleri Açıklama Dili aracını kullanarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="ce0af-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="ce0af-127">Örneğin, XML Web hizmeti URL'SİNDE açılırsa `http://myserver/data/DataSetSample.asmx`, Visual Basic .NET Ara sunucu ile bir ad alanı oluşturmak için komutu aşağıdaki gibi **WebData.DSSample** ve dosya sample.vb içinde depolar.</span><span class="sxs-lookup"><span data-stu-id="ce0af-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="ce0af-128">İçinde dosya sample.cs bir C# proxy oluşturmak için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ce0af-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="ce0af-129">Proxy kitaplık olarak derlenmiş ve XML Web hizmeti istemcisine içeri aktarıldı.</span><span class="sxs-lookup"><span data-stu-id="ce0af-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="ce0af-130">Sample.vb mylib.dll olarak depolanan Visual Basic .NET proxy Kodu derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ce0af-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="ce0af-131">C# proxy kodu sample.cs mylib.dll olarak depolanan derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ce0af-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  <span data-ttu-id="ce0af-132">Bir XML Web hizmeti istemcisi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ce0af-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="ce0af-133">Visual Studio Web hizmeti proxy sınıfı oluşturmak istiyorsanız, yalnızca istemci projesi oluşturun ve Çözüm Gezgini penceresinde projeye sağ tıklayın, **Web başvurusu Ekle'yi**, Web hizmetinden seçin Listenin mevcut Web Hizmetleri (Web hizmeti geçerli çözüm içindeki ya da geçerli bilgisayarda mevcut değilse bu Web Hizmeti uç noktası adresini sağlayan gerektirebilir.) XML Web hizmeti proxy kendiniz (önceki adımda açıklandığı gibi) oluşturmak, istemci kodunuz içeri aktarabilir ve XML Web hizmeti yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce0af-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="ce0af-134">Aşağıdaki örnek kod çağrıları proxy kitaplığı içeri aktarır **GetCustomers** yeni bir müşteri ve döndürür, müşterilerin listesini almak için ekler bir **veri kümesi** güncelleştirmelerle **UpdateCustomers** .</span><span class="sxs-lookup"><span data-stu-id="ce0af-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="ce0af-135">Örnek geçirir bildirimi **veri kümesi** tarafından döndürülen **DataSet.GetChanges** için **UpdateCustomers** yalnızca değiştirilen satırları geçirilmesi gerektiğinden  **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="ce0af-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="ce0af-136">**UpdateCustomers** çözümlenen döndürür **veri kümesi**, daha sonra hangi **birleştirme** varolan içine **veri kümesi** çözümlenen değişiklikler ve herhangi bir araya Satır hatası bilgileri Update.</span><span class="sxs-lookup"><span data-stu-id="ce0af-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="ce0af-137">Aşağıdaki kod, Web başvuru oluşturmak için Visual Studio'yu kullandınız ve DsSample içinde Web başvurusunu yeniden varsayar **Web başvurusu Ekle'yi** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="ce0af-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="ce0af-138">Proxy sınıfı kendiniz oluşturmaya karar verirseniz, aşağıdaki ek adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce0af-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="ce0af-139">Örneği derlemek için (mylib.dll) oluşturulan proxy kitaplığı ve ilgili .NET kitaplıkları'nı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ce0af-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="ce0af-140">Dosya client.vb içinde depolanan örnek, Visual Basic .NET sürümünü derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ce0af-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="ce0af-141">Dosya client.cs içinde depolanan örnek, C# sürümü derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ce0af-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ce0af-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce0af-142">See Also</span></span>  
 [<span data-ttu-id="ce0af-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce0af-143">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="ce0af-144">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="ce0af-144">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="ce0af-145">DataTables</span><span class="sxs-lookup"><span data-stu-id="ce0af-145">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="ce0af-146">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="ce0af-146">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="ce0af-147">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="ce0af-147">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="ce0af-148">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="ce0af-148">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="ce0af-149">Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)</span><span class="sxs-lookup"><span data-stu-id="ce0af-149">Web Services Description Language Tool (Wsdl.exe)</span></span>](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [<span data-ttu-id="ce0af-150">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="ce0af-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
