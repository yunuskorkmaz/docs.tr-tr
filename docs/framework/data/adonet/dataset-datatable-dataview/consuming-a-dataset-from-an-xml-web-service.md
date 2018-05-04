---
title: XML Web hizmetinden veri kümesi kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: da3eca875df9b80f66241a2ecb72c5ba5c1df309
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>XML Web hizmetinden veri kümesi kullanma
<xref:System.Data.DataSet> Kısmen Kolay Aktarım verilerin Internet üzerinden kolaylaştırmak için bağlantısı kesik bir tasarım, tasarlanmış. **DataSet** bir girdi olarak belirtilebilir veya ek bir kodlama olmadan XML Web Hizmetleri çıktısını gerekli içeriğini akışını sağlamak için "seri hale getirilebilir" olan **DataSet** bir XML Web hizmeti bir istemci ve geri. **DataSet** biçimini kullanarak bir XML akışı örtük olarak dönüştürülen, ağ üzerinden gönderilen ve XML akışından yeniden bir **DataSet** alan uçta. Bu, çok basit ve esnek bir yöntemdir iletmek ve XML Web Hizmetleri ile ilişkisel veri döndürmek için sunar. Biçimini hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 Aşağıdaki örnek bir XML Web hizmeti ve Kullan istemci nasıl oluşturulacağını gösterir **DataSet** (değiştirilen veriler dahil) ilişkisel veri taşıma ve herhangi bir güncelleştirme özgün veri kaynağına geri çözümlemek için.  
  
> [!NOTE]
>  Her zaman güvenlik uygulamalarını XML Web Hizmetleri oluştururken ele almanızı öneririz. XML Web Hizmetleri güvenliğini sağlama konusunda daha fazla bilgi için bkz: [güvenli hale getirme XML Web Hizmetleri oluşturulan kullanarak ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Bir veri kümesi kullanır ve döndüren bir XML Web hizmeti oluşturmak için  
  
1.  XML Web hizmeti oluşturun.  
  
     Örnekte, XML Web Hizmetleri veri, bu durumda müşterilerden listesi döndüren oluşturulur **Northwind** veritabanı ve alan bir **DataSet** verilere güncelleştirmeleriyle hangi XML Web hizmeti Özgün veri kaynağına çözümler.  
  
     XML Web hizmetini iki yöntem sunar: **GetCustomers**, müşteriler, listesini döndürmek için ve **UpdateCustomers**, veri kaynağına geri güncelleştirmeleri çözümlemek için. XML Web hizmeti DataSetSample.asmx adlı Web sunucusu üzerinde bir dosyada depolanır. Aşağıdaki kod DataSetSample.asmx içeriğini özetlenmektedir.  
  
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
  
     Tipik bir senaryoda, **UpdateCustomers** yöntemi iyimser eşzamanlılık ihlalleri yakalamak için yazılması. Kolaylık olması için bu örnek içermez. İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  XML Web hizmeti proxy'si oluşturun.  
  
     XML Web hizmetinin istemciler sunulan yöntemleri kullanmak için bir SOAP proxy gerektirir. Visual Studio sizin için bu proxy oluşturmak olabilir. Bir varolan Web hizmetinden Visual Studio'dan bir Web başvuru ayarlayarak, bu adımda açıklanan tüm davranış şeffaf bir şekilde gerçekleşir. Proxy sınıfı kendiniz oluşturmak istiyorsanız, bu tartışma ile devam edin. Çoğu durumda, ancak, istemci uygulaması proxy sınıfı oluşturmak için Visual Studio kullanarak yeterli olur.  
  
     Bir proxy Web Hizmetleri Açıklama Dili aracını kullanarak oluşturulabilir. XML Web hizmeti URL'de açılırsa örneğin http://myserver/data/DataSetSample.asmx, ad alanı ile bir Visual Basic .NET proxy oluşturmak için komutu aşağıdaki gibi **WebData.DSSample** ve dosya sample.vb saklayın.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Bir C# proxy dosya sample.cs oluşturmak için aşağıdaki komutu yürütün.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy kitaplık olarak derlenmiş ve XML Web hizmeti istemcisine alındı. Sample.vb sample.dll olarak depolanan Visual Basic .NET proxy Kodu derlemek için aşağıdaki komutu yürütün.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     C# proxy kodu sample.cs sample.dll olarak depolanan derlemek için aşağıdaki komutu yürütün.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  XML Web hizmeti istemcisi oluşturun.  
  
     Visual Studio Web hizmeti proxy sınıfı oluşturmak istiyorsanız, yalnızca istemci projesi oluşturun ve Çözüm Gezgini penceresinde projesine sağ tıklayın, **Web Başvuru Ekle**, Web hizmetinden seçin Listenin kullanılabilir Web Hizmetleri (Web hizmeti geçerli çözümde ya da geçerli bilgisayarda kullanılabilir durumda olmazsa bu Web Hizmeti uç noktası adresi gerektirebilir.) Varsa XML Web hizmeti proxy'si kendiniz (önceki adımda açıklandığı gibi) oluşturmak, istemci kodunuza içeri aktarabilir ve XML Web hizmeti yöntemleri kullanabilir. Aşağıdaki örnek kod proxy Kitaplığı ' çağrıları alır **GetCustomers** müşteriler, listesini almak için yeni bir müşteri ve döndürür ekler bir **DataSet** Güncelleştirmeler ile **UpdateCustomers** .  
  
     Örnek geçirir bildirimi **DataSet** tarafından döndürülen **DataSet.GetChanges** için **UpdateCustomers** yalnızca değiştirilen satırları geçirilecek gerektiğinden  **UpdateCustomers**. **UpdateCustomers** çözülmüş döndürür **DataSet**, daha sonra **birleştirme** varolan içine **DataSet** çözümlenen değişiklikler ve tüm birleştirmek için Güncelleştirme satır hata bilgileri. Aşağıdaki kod Web başvurusu oluşturmak için Visual Studio'yu kullandınız ve DsSample içinde Web başvurusunu adlandırdınız varsayar **Web Başvuru Ekle** iletişim kutusu.  
  
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
  
     Proxy sınıfı kendiniz oluşturmanız karar verirseniz, aşağıdaki ek adımları izlemelisiniz. Örnek derlemek için (sample.dll) oluşturulmuş proxy kitaplığı ve ilgili .NET kitaplıklarına sağlayın. Dosya client.vb içinde depolanan örnek, Visual Basic .NET sürümü derlemek için aşağıdaki komutu yürütün.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     C# sürümü dosya client.cs içinde depolanan örnek derlemek için aşağıdaki komutu yürütün.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [DataAdapter’dan bir DataSet Doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [DataAdapter Parametreleri](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
