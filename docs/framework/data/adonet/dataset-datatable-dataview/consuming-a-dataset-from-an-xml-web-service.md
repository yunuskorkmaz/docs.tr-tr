---
title: "XML Web hizmetinden veri kümesi kullanma"
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
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 316bebfec652987351e64368c3b7c0155011fe8e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="e08df-102">XML Web hizmetinden veri kümesi kullanma</span><span class="sxs-lookup"><span data-stu-id="e08df-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="e08df-103"><xref:System.Data.DataSet> Kısmen Kolay Aktarım verilerin Internet üzerinden kolaylaştırmak için bağlantısı kesik bir tasarım, tasarlanmış.</span><span class="sxs-lookup"><span data-stu-id="e08df-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="e08df-104">**DataSet** bir girdi olarak belirtilebilir veya ek bir kodlama olmadan XML Web Hizmetleri çıktısını gerekli içeriğini akışını sağlamak için "seri hale getirilebilir" olan **DataSet** bir XML Web hizmeti bir istemci ve geri.</span><span class="sxs-lookup"><span data-stu-id="e08df-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="e08df-105">**DataSet** biçimini kullanarak bir XML akışı örtük olarak dönüştürülen, ağ üzerinden gönderilen ve XML akışından yeniden bir **DataSet** alan uçta.</span><span class="sxs-lookup"><span data-stu-id="e08df-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="e08df-106">Bu, çok basit ve esnek bir yöntemdir iletmek ve XML Web Hizmetleri ile ilişkisel veri döndürmek için sunar.</span><span class="sxs-lookup"><span data-stu-id="e08df-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="e08df-107">Biçimini hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="e08df-107">For more information about the DiffGram format, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>  
  
 <span data-ttu-id="e08df-108">Aşağıdaki örnek bir XML Web hizmeti ve Kullan istemci nasıl oluşturulacağını gösterir **DataSet** (değiştirilen veriler dahil) ilişkisel veri taşıma ve herhangi bir güncelleştirme özgün veri kaynağına geri çözümlemek için.</span><span class="sxs-lookup"><span data-stu-id="e08df-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e08df-109">Her zaman güvenlik uygulamalarını XML Web Hizmetleri oluştururken ele almanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e08df-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="e08df-110">XML Web Hizmetleri güvenliğini sağlama konusunda daha fazla bilgi için bkz: [güvenli hale getirme XML Web Hizmetleri oluşturulan kullanarak ASP.NET](http://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span><span class="sxs-lookup"><span data-stu-id="e08df-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](http://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="e08df-111">Bir veri kümesi kullanır ve döndüren bir XML Web hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e08df-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1.  <span data-ttu-id="e08df-112">XML Web hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e08df-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="e08df-113">Örnekte, XML Web Hizmetleri veri, bu durumda müşterilerden listesi döndüren oluşturulur **Northwind** veritabanı ve alan bir **DataSet** verilere güncelleştirmeleriyle hangi XML Web hizmeti Özgün veri kaynağına çözümler.</span><span class="sxs-lookup"><span data-stu-id="e08df-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="e08df-114">XML Web hizmetini iki yöntem sunar: **GetCustomers**, müşteriler, listesini döndürmek için ve **UpdateCustomers**, veri kaynağına geri güncelleştirmeleri çözümlemek için.</span><span class="sxs-lookup"><span data-stu-id="e08df-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="e08df-115">XML Web hizmeti DataSetSample.asmx adlı Web sunucusu üzerinde bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="e08df-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="e08df-116">Aşağıdaki kod DataSetSample.asmx içeriğini özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e08df-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="e08df-117">Tipik bir senaryoda, **UpdateCustomers** yöntemi iyimser eşzamanlılık ihlalleri yakalamak için yazılması.</span><span class="sxs-lookup"><span data-stu-id="e08df-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="e08df-118">Kolaylık olması için bu örnek içermez.</span><span class="sxs-lookup"><span data-stu-id="e08df-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="e08df-119">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="e08df-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span></span>  
  
2.  <span data-ttu-id="e08df-120">XML Web hizmeti proxy'si oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e08df-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="e08df-121">XML Web hizmetinin istemciler sunulan yöntemleri kullanmak için bir SOAP proxy gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e08df-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="e08df-122">Visual Studio sizin için bu proxy oluşturmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="e08df-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="e08df-123">Bir varolan Web hizmetinden Visual Studio'dan bir Web başvuru ayarlayarak, bu adımda açıklanan tüm davranış şeffaf bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e08df-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="e08df-124">Proxy sınıfı kendiniz oluşturmak istiyorsanız, bu tartışma ile devam edin.</span><span class="sxs-lookup"><span data-stu-id="e08df-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="e08df-125">Çoğu durumda, ancak, istemci uygulaması proxy sınıfı oluşturmak için Visual Studio kullanarak yeterli olur.</span><span class="sxs-lookup"><span data-stu-id="e08df-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="e08df-126">Bir proxy Web Hizmetleri Açıklama Dili aracını kullanarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e08df-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="e08df-127">XML Web hizmeti URL'si http://myserver/data/DataSetSample.asmx açılırsa, örneğin, bir Visual Basic .NET proxy bir ad alanı oluşturmak için bir komut aşağıdaki gibi sorun **WebData.DSSample** ve dosyasında depolamak Sample.vb.</span><span class="sxs-lookup"><span data-stu-id="e08df-127">For example, if the XML Web service is exposed at the URL http://myserver/data/DataSetSample.asmx, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```  
    wsdl /l:VB /out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="e08df-128">Bir C# proxy dosya sample.cs oluşturmak için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="e08df-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```  
    wsdl /l:CS /out:sample.cs http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="e08df-129">Proxy kitaplık olarak derlenmiş ve XML Web hizmeti istemcisine alındı.</span><span class="sxs-lookup"><span data-stu-id="e08df-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="e08df-130">Sample.vb sample.dll olarak depolanan Visual Basic .NET proxy Kodu derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="e08df-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```  
    vbc /t:library /out:sample.dll sample.vb /r:System.dll /r:System.Web.Services.dll /r:System.Data.dll /r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="e08df-131">C# proxy kodu sample.cs sample.dll olarak depolanan derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="e08df-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```  
    csc /t:library /out:sample.dll sample.cs /r:System.dll /r:System.Web.Services.dll /r:System.Data.dll /r:System.Xml.dll  
    ```  
  
3.  <span data-ttu-id="e08df-132">XML Web hizmeti istemcisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e08df-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="e08df-133">Visual Studio Web hizmeti proxy sınıfı oluşturmak istiyorsanız, yalnızca istemci projesi oluşturun ve Çözüm Gezgini penceresinde projesine sağ tıklayın, **Web Başvuru Ekle**, Web hizmetinden seçin Listenin kullanılabilir Web Hizmetleri (Web hizmeti geçerli çözümde ya da geçerli bilgisayarda kullanılabilir durumda olmazsa bu Web Hizmeti uç noktası adresi gerektirebilir.) Varsa XML Web hizmeti proxy'si kendiniz (önceki adımda açıklandığı gibi) oluşturmak, istemci kodunuza içeri aktarabilir ve XML Web hizmeti yöntemleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e08df-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="e08df-134">Aşağıdaki örnek kod proxy Kitaplığı ' çağrıları alır **GetCustomers** müşteriler, listesini almak için yeni bir müşteri ve döndürür ekler bir **DataSet** Güncelleştirmeler ile **UpdateCustomers** .</span><span class="sxs-lookup"><span data-stu-id="e08df-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="e08df-135">Örnek geçirir bildirimi **DataSet** tarafından döndürülen **DataSet.GetChanges** için **UpdateCustomers** yalnızca değiştirilen satırları geçirilecek gerektiğinden  **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="e08df-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="e08df-136">**UpdateCustomers** çözülmüş döndürür **DataSet**, hangi daha sonra **birleştirme** varolan içine **DataSet** çözülmüş değişikliklerin uygulanması için ve Güncelleştirme hiçbir satır hata bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e08df-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="e08df-137">Aşağıdaki kod Web başvurusu oluşturmak için Visual Studio'yu kullandınız ve DsSample içinde Web başvurusunu adlandırdınız varsayar **Web Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e08df-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="e08df-138">Proxy sınıfı kendiniz oluşturmanız karar verirseniz, aşağıdaki ek adımları izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e08df-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="e08df-139">Örnek derlemek için (sample.dll) oluşturulmuş proxy kitaplığı ve ilgili .NET kitaplıklarına sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e08df-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="e08df-140">Dosya client.vb içinde depolanan örnek, Visual Basic .NET sürümü derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="e08df-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```  
    vbc client.vb /r:sample.dll /r:System.dll /r:System.Data.dll /r:System.Xml.dll /r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="e08df-141">C# sürümü dosya client.cs içinde depolanan örnek derlemek için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="e08df-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```  
    csc client.cs /r:sample.dll /r:System.dll /r:System.Data.dll /r:System.Xml.dll /r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e08df-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e08df-142">See Also</span></span>  
 [<span data-ttu-id="e08df-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e08df-143">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="e08df-144">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="e08df-144">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="e08df-145">DataTables</span><span class="sxs-lookup"><span data-stu-id="e08df-145">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="e08df-146">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="e08df-146">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="e08df-147">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="e08df-147">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="e08df-148">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="e08df-148">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="e08df-149">Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)</span><span class="sxs-lookup"><span data-stu-id="e08df-149">Web Services Description Language Tool (Wsdl.exe)</span></span>](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [<span data-ttu-id="e08df-150">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="e08df-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
