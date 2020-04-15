---
title: XML Web Hizmetinden DataSet Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d7328949e3eb4822b1a645bb5f0c1866f01ecb0a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389745"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="577ee-102">Bir XML web hizmetinden Bir DataSet tüketin</span><span class="sxs-lookup"><span data-stu-id="577ee-102">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="577ee-103">Kısmen <xref:System.Data.DataSet> Internet üzerinden veri rahat aktarım kolaylaştırmak için, bağlantısız bir tasarım ile mimarı oldu.</span><span class="sxs-lookup"><span data-stu-id="577ee-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="577ee-104">**DataSet,** **XML** Web hizmetinin içeriğini bir XML Web hizmetinden istemciye ve geri akışı için gerekli ek kodlama olmadan XML Web hizmetlerine giriş veya çıktı olarak belirtilebildiği için "serileştirilebilir".</span><span class="sxs-lookup"><span data-stu-id="577ee-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="577ee-105">**DataSet,** DiffGram biçimini kullanarak dolaylı olarak XML akışına dönüştürülür, ağ üzerinden gönderilir ve ardından xml akışından alıcı uçta **DataSet** olarak yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="577ee-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="577ee-106">Bu, XML Web hizmetlerini kullanarak ilişkisel verileri iletmek ve döndürmek için çok basit ve esnek bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="577ee-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="577ee-107">DiffGram biçimi hakkında daha fazla bilgi için [DiffGrams'a](diffgrams.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="577ee-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="577ee-108">Aşağıdaki örnek, İlişkisel verileri (değiştirilmiş veriler dahil) taşımak ve güncelleştirmeleri özgün veri kaynağına geri çözmek için **DataSet'i** kullanan bir XML Web hizmeti ve istemcisinin nasıl oluşturuldestekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="577ee-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="577ee-109">Bir XML Web hizmeti oluştururken güvenlik etkilerini her zaman göz önünde bulundurmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="577ee-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="577ee-110">Bir XML Web hizmetinin güvenliğini sağlama hakkında bilgi için bkz: [ASP.NET kullanılarak oluşturulan XML Web Hizmetlerini Güvence Altına Alma.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="577ee-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="577ee-111">Bir XML web hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="577ee-111">Create an XML web service</span></span>
  
1. <span data-ttu-id="577ee-112">XML Web hizmetini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="577ee-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="577ee-113">Örnekte, verileri döndüren bir XML Web hizmeti oluşturulur, bu durumda **Northwind** veritabanından bir müşteri listesi ve XML Web hizmetinin özgün veri kaynağına geri çözeceği veri güncelleştirmelerini içeren bir **DataSet** alır.</span><span class="sxs-lookup"><span data-stu-id="577ee-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="577ee-114">XML Web hizmeti iki yöntem ortaya çıkarır: **GetCustomers**, müşteri listesini döndürmek için, ve **UpdateCustomers**, veri kaynağına güncellemeleri geri çözmek için.</span><span class="sxs-lookup"><span data-stu-id="577ee-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="577ee-115">XML Web hizmeti, Web sunucusunda DataSetSample.asmx adlı bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="577ee-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="577ee-116">Aşağıdaki kod DataSetSample.asmx içeriğini özetliyor.</span><span class="sxs-lookup"><span data-stu-id="577ee-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="577ee-117">Tipik bir senaryoda, İyimser eşzamanlılık ihlallerini yakalamak için **UpdateCustomers** yöntemi yazılır.</span><span class="sxs-lookup"><span data-stu-id="577ee-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="577ee-118">Basitlik için, örnek bu içermez.</span><span class="sxs-lookup"><span data-stu-id="577ee-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="577ee-119">İyimser eşzamanlılık hakkında daha fazla bilgi [için, Bkz. İyimser Eşzamanlılık.](../optimistic-concurrency.md)</span><span class="sxs-lookup"><span data-stu-id="577ee-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="577ee-120">Bir XML Web hizmeti proxy'si oluşturun.</span><span class="sxs-lookup"><span data-stu-id="577ee-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="577ee-121">XML Web hizmetinin istemcileri, maruz kalan yöntemleri tüketmek için bir SOAP proxy'si gerektirir.</span><span class="sxs-lookup"><span data-stu-id="577ee-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="577ee-122">Visual Studio sizin için bu proxy oluşturmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="577ee-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="577ee-123">Visual Studio içinden varolan bir Web hizmetine Web başvurusu ayarlayarak, bu adımda açıklanan tüm davranış saydam olarak oluşur.</span><span class="sxs-lookup"><span data-stu-id="577ee-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="577ee-124">Proxy sınıfını kendiniz oluşturmak istiyorsanız, bu tartışmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="577ee-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="577ee-125">Çoğu durumda, ancak, istemci uygulaması için proxy sınıfı oluşturmak için Visual Studio kullanarak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="577ee-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="577ee-126">Web Hizmetleri Açıklama Dil Aracı kullanılarak proxy oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="577ee-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="577ee-127">Örneğin, XML Web hizmeti URL'de `http://myserver/data/DataSetSample.asmx`açıklanırsa, **WebData.DSSample** ad alanına sahip bir Visual Basic .NET proxy oluşturmak ve dosya örneğinde depolamak için aşağıdaki gibi bir komut verin.</span><span class="sxs-lookup"><span data-stu-id="577ee-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="577ee-128">Dosyada sample.cs c# proxy'si oluşturmak için aşağıdaki komutu girin.</span><span class="sxs-lookup"><span data-stu-id="577ee-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="577ee-129">Proxy daha sonra kitaplık olarak derlenebilir ve XML Web hizmeti istemcisine aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="577ee-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="577ee-130">sample.vb'de depolanan Visual Basic .NET proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="577ee-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="577ee-131">sample.cs'da depolanan C# proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="577ee-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="577ee-132">Bir XML Web hizmeti istemcisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="577ee-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="577ee-133">Visual Studio'nun sizin için Web hizmeti proxy sınıfını oluşturmasını istiyorsanız, istemci projesini oluşturmanız ve Çözüm Gezgini penceresinde projeyi sağ tıklatın ve ardından**Hizmet Başvurusu** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="577ee-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="577ee-134">Hizmet **Başvurusu Ekle** iletişim kutusunda **Gelişmiş**'i seçin ve ardından **Web Başvurusu Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="577ee-134">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="577ee-135">Kullanılabilir Web hizmetleri listesinden Web hizmetini seçin (Bu, Web hizmeti geçerli çözümde veya geçerli bilgisayarda kullanılamıyorsa Web hizmeti bitiş noktasının adresini nsağlanmasını gerektirebilir).</span><span class="sxs-lookup"><span data-stu-id="577ee-135">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="577ee-136">XML Web hizmeti proxy'sini kendiniz oluşturursanız (önceki adımda açıklandığı gibi), istemci kodunuza aktarabilir ve XML Web hizmet yöntemlerini tüketebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="577ee-136">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="577ee-137">Aşağıdaki örnek kod proxy kitaplığını alır, **GetCustomers'i** müşterilerin listesini almak için arar, yeni bir müşteri ekler ve **updatecustomers'e**güncelleştirmelerle birlikte bir **DataSet** döndürür.</span><span class="sxs-lookup"><span data-stu-id="577ee-137">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="577ee-138">Yalnızca değiştirilen satırların **UpdateCustomers'e**geçirilmesi gerektiğinden, veriseti tarafından döndürülen **DataSet'ten** **DataSet.GetChanges** **UpdateCustomers'e** geçer.</span><span class="sxs-lookup"><span data-stu-id="577ee-138">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="577ee-139">**UpdateCustomers,** çözülmüş değişiklikleri ve güncelleştirmedeki satır hata bilgilerini birleştirmek için varolan DataSet'te **birleştirebileceğiniz** çözülmüş **DataSet'i**döndürür. **DataSet**</span><span class="sxs-lookup"><span data-stu-id="577ee-139">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="577ee-140">Aşağıdaki kod, Web başvurusunu oluşturmak için Visual Studio'yu kullandığınızı ve Web Başvuru **Ekle** iletişim kutusunda Ki Web başvurusunu DsSample olarak yeniden adlandırdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="577ee-140">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="577ee-141">Proxy sınıfını kendiniz oluşturmaya karar verirseniz, aşağıdaki ek adımları atmalısınız.</span><span class="sxs-lookup"><span data-stu-id="577ee-141">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="577ee-142">Örneği derlemek için oluşturulan proxy kitaplığını (sample.dll) ve ilgili .NET kitaplıklarını verin.</span><span class="sxs-lookup"><span data-stu-id="577ee-142">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="577ee-143">Client.vb dosyasında depolanan örneğin Visual Basic .NET sürümünü derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="577ee-143">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="577ee-144">Client.cs dosyada depolanan örneğin C# sürümünü derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="577ee-144">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="577ee-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="577ee-145">See also</span></span>

- [<span data-ttu-id="577ee-146">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="577ee-146">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="577ee-147">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="577ee-147">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="577ee-148">DataTables</span><span class="sxs-lookup"><span data-stu-id="577ee-148">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="577ee-149">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="577ee-149">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="577ee-150">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="577ee-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="577ee-151">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="577ee-151">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="577ee-152">[Web Hizmetleri Açıklama Dil Aracı (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="577ee-152">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="577ee-153">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="577ee-153">ADO.NET Overview</span></span>](../ado-net-overview.md)
