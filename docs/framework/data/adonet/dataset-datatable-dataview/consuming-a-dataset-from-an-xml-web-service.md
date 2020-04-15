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
# <a name="consume-a-dataset-from-an-xml-web-service"></a>Bir XML web hizmetinden Bir DataSet tüketin

Kısmen <xref:System.Data.DataSet> Internet üzerinden veri rahat aktarım kolaylaştırmak için, bağlantısız bir tasarım ile mimarı oldu. **DataSet,** **XML** Web hizmetinin içeriğini bir XML Web hizmetinden istemciye ve geri akışı için gerekli ek kodlama olmadan XML Web hizmetlerine giriş veya çıktı olarak belirtilebildiği için "serileştirilebilir". **DataSet,** DiffGram biçimini kullanarak dolaylı olarak XML akışına dönüştürülür, ağ üzerinden gönderilir ve ardından xml akışından alıcı uçta **DataSet** olarak yeniden oluşturulur. Bu, XML Web hizmetlerini kullanarak ilişkisel verileri iletmek ve döndürmek için çok basit ve esnek bir yöntem sağlar. DiffGram biçimi hakkında daha fazla bilgi için [DiffGrams'a](diffgrams.md)bakın.  
  
 Aşağıdaki örnek, İlişkisel verileri (değiştirilmiş veriler dahil) taşımak ve güncelleştirmeleri özgün veri kaynağına geri çözmek için **DataSet'i** kullanan bir XML Web hizmeti ve istemcisinin nasıl oluşturuldestekleyeceğini gösterir.  
  
> [!NOTE]
> Bir XML Web hizmeti oluştururken güvenlik etkilerini her zaman göz önünde bulundurmanızı öneririz. Bir XML Web hizmetinin güvenliğini sağlama hakkında bilgi için bkz: [ASP.NET kullanılarak oluşturulan XML Web Hizmetlerini Güvence Altına Alma.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))  
  
## <a name="create-an-xml-web-service"></a>Bir XML web hizmeti oluşturma
  
1. XML Web hizmetini oluşturun.  
  
     Örnekte, verileri döndüren bir XML Web hizmeti oluşturulur, bu durumda **Northwind** veritabanından bir müşteri listesi ve XML Web hizmetinin özgün veri kaynağına geri çözeceği veri güncelleştirmelerini içeren bir **DataSet** alır.  
  
     XML Web hizmeti iki yöntem ortaya çıkarır: **GetCustomers**, müşteri listesini döndürmek için, ve **UpdateCustomers**, veri kaynağına güncellemeleri geri çözmek için. XML Web hizmeti, Web sunucusunda DataSetSample.asmx adlı bir dosyada depolanır. Aşağıdaki kod DataSetSample.asmx içeriğini özetliyor.  
  
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
  
     Tipik bir senaryoda, İyimser eşzamanlılık ihlallerini yakalamak için **UpdateCustomers** yöntemi yazılır. Basitlik için, örnek bu içermez. İyimser eşzamanlılık hakkında daha fazla bilgi [için, Bkz. İyimser Eşzamanlılık.](../optimistic-concurrency.md)  
  
2. Bir XML Web hizmeti proxy'si oluşturun.  
  
     XML Web hizmetinin istemcileri, maruz kalan yöntemleri tüketmek için bir SOAP proxy'si gerektirir. Visual Studio sizin için bu proxy oluşturmak olabilir. Visual Studio içinden varolan bir Web hizmetine Web başvurusu ayarlayarak, bu adımda açıklanan tüm davranış saydam olarak oluşur. Proxy sınıfını kendiniz oluşturmak istiyorsanız, bu tartışmaya devam edin. Çoğu durumda, ancak, istemci uygulaması için proxy sınıfı oluşturmak için Visual Studio kullanarak yeterlidir.  
  
     Web Hizmetleri Açıklama Dil Aracı kullanılarak proxy oluşturulabilir. Örneğin, XML Web hizmeti URL'de `http://myserver/data/DataSetSample.asmx`açıklanırsa, **WebData.DSSample** ad alanına sahip bir Visual Basic .NET proxy oluşturmak ve dosya örneğinde depolamak için aşağıdaki gibi bir komut verin.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Dosyada sample.cs c# proxy'si oluşturmak için aşağıdaki komutu girin.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy daha sonra kitaplık olarak derlenebilir ve XML Web hizmeti istemcisine aktarılabilir. sample.vb'de depolanan Visual Basic .NET proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     sample.cs'da depolanan C# proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Bir XML Web hizmeti istemcisi oluşturun.  
  
     Visual Studio'nun sizin için Web hizmeti proxy sınıfını oluşturmasını istiyorsanız, istemci projesini oluşturmanız ve Çözüm Gezgini penceresinde projeyi sağ tıklatın ve ardından**Hizmet Başvurusu** **Ekle'yi** > seçin. Hizmet **Başvurusu Ekle** iletişim kutusunda **Gelişmiş**'i seçin ve ardından **Web Başvurusu Ekle'yi**seçin. Kullanılabilir Web hizmetleri listesinden Web hizmetini seçin (Bu, Web hizmeti geçerli çözümde veya geçerli bilgisayarda kullanılamıyorsa Web hizmeti bitiş noktasının adresini nsağlanmasını gerektirebilir). XML Web hizmeti proxy'sini kendiniz oluşturursanız (önceki adımda açıklandığı gibi), istemci kodunuza aktarabilir ve XML Web hizmet yöntemlerini tüketebilirsiniz.

     Aşağıdaki örnek kod proxy kitaplığını alır, **GetCustomers'i** müşterilerin listesini almak için arar, yeni bir müşteri ekler ve **updatecustomers'e**güncelleştirmelerle birlikte bir **DataSet** döndürür.  
  
     Yalnızca değiştirilen satırların **UpdateCustomers'e**geçirilmesi gerektiğinden, veriseti tarafından döndürülen **DataSet'ten** **DataSet.GetChanges** **UpdateCustomers'e** geçer. **UpdateCustomers,** çözülmüş değişiklikleri ve güncelleştirmedeki satır hata bilgilerini birleştirmek için varolan DataSet'te **birleştirebileceğiniz** çözülmüş **DataSet'i**döndürür. **DataSet** Aşağıdaki kod, Web başvurusunu oluşturmak için Visual Studio'yu kullandığınızı ve Web Başvuru **Ekle** iletişim kutusunda Ki Web başvurusunu DsSample olarak yeniden adlandırdığınızı varsayar.  
  
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
  
     Proxy sınıfını kendiniz oluşturmaya karar verirseniz, aşağıdaki ek adımları atmalısınız. Örneği derlemek için oluşturulan proxy kitaplığını (sample.dll) ve ilgili .NET kitaplıklarını verin. Client.vb dosyasında depolanan örneğin Visual Basic .NET sürümünü derlemek için aşağıdaki komutu verin.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Client.cs dosyada depolanan örneğin C# sürümünü derlemek için aşağıdaki komutu verin.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](../index.md)
- [DataSets, DataTables ve DataViews](index.md)
- [DataTables](datatables.md)
- [DataAdapter’dan bir DataSet Doldurma](../populating-a-dataset-from-a-dataadapter.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../updating-data-sources-with-dataadapters.md)
- [DataAdapter Parametreleri](../dataadapter-parameters.md)
- [Web Hizmetleri Açıklama Dil Aracı (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
