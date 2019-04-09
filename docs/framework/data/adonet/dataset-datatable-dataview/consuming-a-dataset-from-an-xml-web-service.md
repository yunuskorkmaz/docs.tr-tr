---
title: XML Web Hizmetinden DataSet Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: e07fd6598d6b2d1bbd52e5e6735264821b8986bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180251"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>XML Web Hizmetinden DataSet Kullanma
<xref:System.Data.DataSet> Kısmen Internet üzerinden veri uygun taşıma kolaylaştırmak için bağlantısı kesik bir tasarım ile için tasarlanmıştır. **Veri kümesi** girdi olarak belirlenebilir veya ek kodlamaya gerek kalmadan, XML Web Hizmetleri çıktısını gerekli içeriğini akışını sağlamak için "seri hale getirilebilir" olan **veri kümesi** bir XML Web hizmeti bir istemci ve arka. **Veri kümesi** örtük olarak biçimini kullanarak bir XML akışı dönüştürülür, ağ üzerinden gönderilen ve ardından XML Akışı'ndan reconstructed bir **veri kümesi** alan uçta. Bu, basit ve esnek bir yöntem iletme ve XML Web Hizmetleri kullanarak ilişkisel verileri döndürmek için sağlar. Biçimini hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 Aşağıdaki örnek, bir XML Web hizmeti ve Kullan istemci oluşturma işlemi gösterilmektedir **veri kümesi** (değiştirilen veriler dahil) ilişkisel verilerin taşınması ve güncelleştirmelerden özgün veri kaynağına geri çözmek için.  
  
> [!NOTE]
>  Biz, her zaman güvenlikle ilgili etkileri XML Web hizmeti oluştururken düşünmenizi öneririz. XML Web hizmeti güvenli hale getirme hakkında daha fazla bilgi için bkz: [güvenli hale getirme XML Web Hizmetleri oluşturulan kullanarak ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Bir veri kümesini kullanan ve döndüren bir XML Web hizmeti oluşturmak için  
  
1.  XML Web hizmeti oluşturun.  
  
     Örnekte, veri, bu durumda, müşterilerin listesini döndüren bir XML Web hizmeti oluşturulur **Northwind** veritabanı ve alan bir **veri kümesi** veri güncelleştirmeleri, XML Web hizmeti Özgün veri kaynağına çözümler.  
  
     XML Web hizmeti iki yöntem sunar: **GetCustomers**, müşteriler, listesini döndürmek için ve **UpdateCustomers**, güncelleştirmeleri veri kaynağına geri çözümlenecek. XML Web hizmeti, Web sunucusunda DataSetSample.asmx adlı bir dosyada depolanır. Aşağıdaki kod DataSetSample.asmx içeriğini açıklar.  
  
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
  
     Tipik bir senaryoda **UpdateCustomers** yöntemi iyimser eşzamanlılık ihlalleri yakalayıp yakalamayacağınıza karar yazılabilir. Kolaylık olması için bu örnek içermez. İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  Bir XML Web hizmeti proxy oluşturma.  
  
     XML Web hizmeti istemcilerine kullanıma sunulan yöntemleri kullanmak için bir SOAP proxy gerektirir. Visual Studio sizin için bu proxy oluşturmak olabilir. Bir mevcut Web hizmetinden Visual Studio'dan bir Web başvurusu ayarlayarak bu adımda açıklandığı gibi davranış şeffaf bir şekilde gerçekleşir. Proxy sınıfı kendiniz oluşturmak istiyorsanız, bu tartışma ile devam edin. Çoğu durumda, ancak istemci uygulamanın proxy sınıfı oluşturmak için Visual Studio kullanarak yeterli olur.  
  
     Bir proxy Web Hizmetleri Açıklama Dili aracını kullanarak oluşturulabilir. Örneğin, XML Web hizmeti URL'SİNDE açılırsa `http://myserver/data/DataSetSample.asmx`, Visual Basic .NET Ara sunucu ile bir ad alanı oluşturmak için komutu aşağıdaki gibi **WebData.DSSample** ve dosya sample.vb içinde depolar.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     İçinde dosya sample.cs bir C# proxy oluşturmak için aşağıdaki komutu yürütün.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy kitaplık olarak derlenmiş ve XML Web hizmeti istemcisine içeri aktarıldı. Sample.vb mylib.dll olarak depolanan Visual Basic .NET proxy Kodu derlemek için aşağıdaki komutu yürütün.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     C# proxy kodu sample.cs mylib.dll olarak depolanan derlemek için aşağıdaki komutu yürütün.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  Bir XML Web hizmeti istemcisi oluşturma.  
  
     Visual Studio Web hizmeti proxy sınıfı oluşturmak istiyorsanız, yalnızca istemci projesi oluşturun ve Çözüm Gezgini penceresinde projeye sağ tıklayın, **Web başvurusu Ekle'yi**, Web hizmetinden seçin Listenin mevcut Web Hizmetleri (Web hizmeti geçerli çözüm içindeki ya da geçerli bilgisayarda mevcut değilse bu Web Hizmeti uç noktası adresini sağlayan gerektirebilir.) XML Web hizmeti proxy kendiniz (önceki adımda açıklandığı gibi) oluşturmak, istemci kodunuz içeri aktarabilir ve XML Web hizmeti yöntemlerini kullanır. Aşağıdaki örnek kod çağrıları proxy kitaplığı içeri aktarır **GetCustomers** yeni bir müşteri ve döndürür, müşterilerin listesini almak için ekler bir **veri kümesi** güncelleştirmelerle **UpdateCustomers** .  
  
     Örnek geçirir bildirimi **veri kümesi** tarafından döndürülen **DataSet.GetChanges** için **UpdateCustomers** yalnızca değiştirilen satırları geçirilmesi gerektiğinden  **UpdateCustomers**. **UpdateCustomers** çözümlenen döndürür **veri kümesi**, daha sonra hangi **birleştirme** varolan içine **veri kümesi** çözümlenen değişiklikler ve herhangi bir araya Satır hatası bilgileri Update. Aşağıdaki kod, Web başvuru oluşturmak için Visual Studio'yu kullandınız ve DsSample içinde Web başvurusunu yeniden varsayar **Web başvurusu Ekle'yi** iletişim kutusu.  
  
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
  
     Proxy sınıfı kendiniz oluşturmaya karar verirseniz, aşağıdaki ek adımları uygulamanız gerekir. Örneği derlemek için (mylib.dll) oluşturulan proxy kitaplığı ve ilgili .NET kitaplıkları'nı sağlayın. Dosya client.vb içinde depolanan örnek, Visual Basic .NET sürümünü derlemek için aşağıdaki komutu yürütün.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Dosya client.cs içinde depolanan örnek, C# sürümü derlemek için aşağıdaki komutu yürütün.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [DataAdapter’dan bir DataSet Doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [DataAdapter Parametreleri](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
