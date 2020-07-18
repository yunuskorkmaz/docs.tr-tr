---
title: XML Web hizmetinden veri kümesi kullanma
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: e6dc32274cc3b0d7ec9d66a837a422c87fb2468b
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416218"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="9d033-102">XML Web hizmetinden veri kümesi kullanma</span><span class="sxs-lookup"><span data-stu-id="9d033-102">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="9d033-103">, <xref:System.Data.DataSet> Internet üzerinden veri aktarımını kolaylaştırmak için kısmen bağlantısız bir tasarıma göre tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d033-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="9d033-104">Veri kümesi, **veri kümesinin** IÇERIĞINI bir XML Web hizmetinden bir istemciye ve geriye doğru akışa almak için gereken ek bir kodlama olmadan XML Web hizmetlerinden bir giriş veya çıkış olarak belirtime için "serileştirilebilir **" olur.**</span><span class="sxs-lookup"><span data-stu-id="9d033-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="9d033-105">**Veri kümesi** örtük olarak, DiffGram biçimi KULLANıLARAK bir XML akışına dönüştürülür, ağ üzerinden gönderilir ve ardından XML akışından alma ucunda bir **veri kümesi** olarak yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d033-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="9d033-106">Bu, XML Web hizmetlerini kullanarak ilişkisel verileri iletmek ve döndürmek için basit ve esnek bir yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="9d033-106">This gives you a simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="9d033-107">DiffGram biçimi hakkında daha fazla bilgi için bkz. [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="9d033-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="9d033-108">Aşağıdaki örnek, ilişkisel verileri (değiştirilen veriler dahil) taşımak için **veri kümesini** kullanan bir XML Web hizmeti ve istemcisinin nasıl oluşturulacağını gösterir ve tüm güncelleştirmeleri özgün veri kaynağına geri çözümler.</span><span class="sxs-lookup"><span data-stu-id="9d033-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d033-109">`DataSet` `DataTable` Girişin güvenilir OLMAMASı durumunda XML Web hizmeti çağrılarının bir parçası olarak iletilmesi veya örnekleri güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="9d033-109">Transmitting `DataSet` or `DataTable` instances as part of XML Web service calls is not safe if the input is not trusted.</span></span> <span data-ttu-id="9d033-110">Daha fazla bilgi için bkz. [DataSet ve DataTable Güvenlik Kılavuzu](security-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="9d033-110">For more information, see [DataSet and DataTable security guidance](security-guidance.md).</span></span>
> <span data-ttu-id="9d033-111">Ayrıca, bir XML Web hizmeti oluştururken her zaman güvenlik etkilerini düşünmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="9d033-111">We also recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="9d033-112">Bir XML Web hizmetinin güvenliğini sağlama hakkında bilgi için bkz. [ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin güvenliğini sağlama](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9d033-112">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="9d033-113">XML Web hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d033-113">Create an XML web service</span></span>
  
1. <span data-ttu-id="9d033-114">XML Web hizmetini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d033-114">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="9d033-115">Örnekte, verileri döndüren bir XML Web hizmeti oluşturulur ve bu durumda **Northwind** veritabanındaki müşterilerin bir listesi bulunur ve XML Web hizmeti 'nin özgün veri kaynağına geri çözümlenen veriler için güncelleştirmeler Içeren bir **veri kümesi** alır.</span><span class="sxs-lookup"><span data-stu-id="9d033-115">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="9d033-116">XML Web hizmeti, güncelleştirmeleri veri kaynağına geri çözümlemek üzere müşteriler ve **UpdateCustomers**listesini döndürmek için iki yöntem sunar: **GetCustomers**.</span><span class="sxs-lookup"><span data-stu-id="9d033-116">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="9d033-117">XML Web hizmeti, Web sunucusunda DataSetSample. asmx adlı bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="9d033-117">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="9d033-118">Aşağıdaki kod, DataSetSample. asmx içeriğini özetler.</span><span class="sxs-lookup"><span data-stu-id="9d033-118">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="9d033-119">Tipik bir senaryoda, iyimser eşzamanlılık ihlallerini yakalamak için **UpdateCustomers** yöntemi yazılır.</span><span class="sxs-lookup"><span data-stu-id="9d033-119">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="9d033-120">Kolaylık olması için örnek bunu içermez.</span><span class="sxs-lookup"><span data-stu-id="9d033-120">For simplicity, the example does not include this.</span></span> <span data-ttu-id="9d033-121">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz. [Iyimser eşzamanlılık](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="9d033-121">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="9d033-122">Bir XML Web hizmeti proxy 'si oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d033-122">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="9d033-123">XML Web hizmeti istemcilerinin, sunulan yöntemleri kullanabilmesi için bir SOAP proxy 'si gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d033-123">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="9d033-124">Bu proxy 'yi sizin için Visual Studio 'Nun oluşturmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d033-124">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="9d033-125">Visual Studio içinden mevcut bir Web hizmetine bir Web başvurusu ayarlayarak, bu adımda açıklanan tüm davranışlar saydam bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9d033-125">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="9d033-126">Proxy sınıfını kendiniz oluşturmak istiyorsanız bu tartışmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="9d033-126">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="9d033-127">Ancak çoğu durumda, istemci uygulaması için proxy sınıfı oluşturmak üzere Visual Studio kullanılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="9d033-127">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="9d033-128">Bir proxy, Web Hizmetleri Açıklama Dili Aracı kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="9d033-128">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="9d033-129">Örneğin, XML Web hizmeti URL 'de açığa çıkarılacaksanız `http://myserver/data/DataSetSample.asmx` , **Webdata. dssample** ad alanı ile Visual Basic .net proxy oluşturmak için aşağıdaki gibi bir komut oluşturun ve bunu Sample. vb dosyasında depolayın.</span><span class="sxs-lookup"><span data-stu-id="9d033-129">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="9d033-130">Sample.cs dosyasında bir C# proxy oluşturmak için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="9d033-130">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="9d033-131">Proxy daha sonra bir kitaplık olarak derlenebilir ve XML Web hizmeti istemcisine aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d033-131">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="9d033-132">Örnek. vb 'de depolanan Visual Basic .NET proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="9d033-132">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="9d033-133">Sample.cs içinde depolanan C# proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="9d033-133">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="9d033-134">Bir XML Web hizmeti istemcisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d033-134">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="9d033-135">Sizin için Visual Studio 'nun Web hizmeti proxy sınıfını oluşturmasını istiyorsanız, yalnızca istemci projesini oluşturun ve Çözüm Gezgini penceresinde projeye sağ tıklayıp **Add**  >  **hizmet başvurusu**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9d033-135">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="9d033-136">**Hizmet başvurusu Ekle** Iletişim kutusunda **Gelişmiş**' i seçin ve ardından **Web başvurusu Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9d033-136">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="9d033-137">Kullanılabilir Web Hizmetleri listesinden Web hizmeti ' ni seçin (Web hizmeti geçerli çözüm içinde veya geçerli bilgisayarda yoksa Web hizmeti uç noktasının adresini sağlamak gerekebilir).</span><span class="sxs-lookup"><span data-stu-id="9d033-137">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="9d033-138">XML Web hizmeti proxy 'sini kendiniz oluşturursanız (önceki adımda açıklandığı gibi), istemci kodunuza içeri aktarabilir ve XML Web hizmeti yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d033-138">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="9d033-139">Aşağıdaki örnek kod, ara kitaplığı içeri aktarır, müşterilerin listesini almak için **GetCustomers** çağırır, yeni bir müşteri ekliyor ve sonra **UpdateCustomers**güncelleştirmeleriyle birlikte bir **veri kümesi** döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="9d033-139">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="9d033-140">Örnek **DataSet. GetChanges** tarafından döndürülen **veri kümesini** **UpdateCustomers** 'e geçirir çünkü yalnızca değiştirilen satırların **UpdateCustomers**'a geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d033-140">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="9d033-141">**UpdateCustomers** , çözümlenen değişiklikleri ve tüm satır hata bilgilerini güncelleştirmeden birleştirmek için, daha sonra mevcut **veri kümesiyle** **birleştirebilen** çözümlenmiş **veri kümesini**döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d033-141">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="9d033-142">Aşağıdaki kod, Web başvurusu oluşturmak için Visual Studio kullandığınızı ve **Web başvurusu Ekle** Iletişim kutusunda dssample için Web başvurusunu yeniden adlandırdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="9d033-142">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="9d033-143">Proxy sınıfını kendiniz oluşturmaya karar verirseniz, aşağıdaki ek adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d033-143">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="9d033-144">Örneği derlemek için, oluşturulan ara sunucu kitaplığını (sample.dll) ve ilgili .NET kitaplıklarını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9d033-144">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="9d033-145">Örneğin, Client. vb dosyasında depolanan örnek Visual Basic .NET sürümünü derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="9d033-145">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="9d033-146">Örneğin, client.cs dosyasında depolanan örnek C# sürümünü derlemek için aşağıdaki komutu verin.</span><span class="sxs-lookup"><span data-stu-id="9d033-146">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9d033-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d033-147">See also</span></span>

- [<span data-ttu-id="9d033-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9d033-148">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="9d033-149">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="9d033-149">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="9d033-150">DataTables</span><span class="sxs-lookup"><span data-stu-id="9d033-150">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="9d033-151">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="9d033-151">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="9d033-152">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="9d033-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="9d033-153">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="9d033-153">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="9d033-154">[Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d033-154">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="9d033-155">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d033-155">ADO.NET Overview</span></span>](../ado-net-overview.md)
