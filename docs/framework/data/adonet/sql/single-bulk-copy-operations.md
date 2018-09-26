---
title: Tekil toplu kopyalama işlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 4b2b35d3ca3f7bea5f64188420c17d386a1afa42
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45971987"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="66489-102">Tekil toplu kopyalama işlemleri</span><span class="sxs-lookup"><span data-stu-id="66489-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="66489-103">Bir SQL Server toplu kopyalama işlemi gerçekleştirmek için en kolay yaklaşım, bir veritabanında tek bir işlem gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="66489-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="66489-104">Varsayılan olarak, toplu kopyalama işlemi yalıtılmış bir işlem olarak gerçekleştirilir: yedekleme, geri fırsat ile işlem temelli olmayan bir şekilde, kopyalama işlemi gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="66489-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66489-105">Bir hata oluştuğunda toplu kopyalama bir kısmını veya tamamını geri alma gerekiyorsa kullanabilirsiniz bir <xref:System.Data.SqlClient.SqlBulkCopy>-yönetilen işlem veya mevcut bir işlem içinde toplu kopyalama işlemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="66489-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="66489-106">**SqlBulkCopy** birlikte çalışacağı <xref:System.Transactions> bağlantı (örtük veya açık) olarak kayıtlı değilse bir **System.Transactions** işlem.</span><span class="sxs-lookup"><span data-stu-id="66489-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="66489-107">Daha fazla bilgi için [işlem ve toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="66489-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="66489-108">Toplu kopyalama işlemi gerçekleştirmeye yönelik genel adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="66489-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1.  <span data-ttu-id="66489-109">Kaynak sunucuya bağlanın ve kopyalanacak verileri alın.</span><span class="sxs-lookup"><span data-stu-id="66489-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="66489-110">Veri de gelebilir başka kaynaklardan gelen alınamazsa bir <xref:System.Data.IDataReader> veya <xref:System.Data.DataTable> nesne.</span><span class="sxs-lookup"><span data-stu-id="66489-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2.  <span data-ttu-id="66489-111">Hedef sunucuya (istediğiniz sürece **SqlBulkCopy** sizin için bir bağlantı kurmak için).</span><span class="sxs-lookup"><span data-stu-id="66489-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3.  <span data-ttu-id="66489-112">Oluşturma bir <xref:System.Data.SqlClient.SqlBulkCopy> nesne, tüm gerekli özellikleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="66489-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4.  <span data-ttu-id="66489-113">Ayarlama **DestinationTableName** hedef tablosu için toplu belirtmek için özelliği ekleme işlemi.</span><span class="sxs-lookup"><span data-stu-id="66489-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5.  <span data-ttu-id="66489-114">Birini çağırın **WriteToServer** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="66489-114">Call one of the **WriteToServer** methods.</span></span>  
  
6.  <span data-ttu-id="66489-115">İsteğe bağlı olarak, özellikleri ve arama güncelleştirmesi **WriteToServer** gerektiği şekilde yeniden.</span><span class="sxs-lookup"><span data-stu-id="66489-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7.  <span data-ttu-id="66489-116">Çağrı <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, veya toplu kopyalama işlemleri içinde sarmalamak bir `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="66489-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="66489-117">Kaynak ve hedef sütun veri türlerini eşleşmesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="66489-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="66489-118">Veri türleri eşleşmiyorsa **SqlBulkCopy** her kaynak değeri tarafından kullanılan kuralları kullanarak hedef veri türüne dönüştürmeye çalışır <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="66489-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="66489-119">Dönüştürmeleri performansını etkileyebilir ve ayrıca beklenmeyen hatalara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="66489-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="66489-120">Örneğin, bir `Double` veri türüne dönüştürülebilir bir `Decimal` veri türü çoğu zaman ama her zaman kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="66489-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66489-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="66489-121">Example</span></span>  
 <span data-ttu-id="66489-122">Aşağıdaki konsol uygulaması kullanarak verileri yüklemek gösterilmiştir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="66489-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="66489-123">Bu örnekte, bir <xref:System.Data.SqlClient.SqlDataReader> veri kopyalamak için kullanılan **Production.Product** tablo SQL Server'daki **AdventureWorks** benzer bir tabloya aynı veritabanında veritabanı.</span><span class="sxs-lookup"><span data-stu-id="66489-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="66489-124">Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="66489-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="66489-125">Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca.</span><span class="sxs-lookup"><span data-stu-id="66489-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="66489-126">Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="66489-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="66489-127">Transact-SQL ve komut sınıfı kullanarak toplu kopyalama işlemi gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="66489-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="66489-128">Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> BULK INSERT deyimini yürütmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66489-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66489-129">Veri kaynağı için dosya sunucusuna göreli yoludur.</span><span class="sxs-lookup"><span data-stu-id="66489-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="66489-130">Toplu kopyalama işleminin başarılı olması için sunucu işlemi bu yola erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66489-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="66489-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66489-131">See Also</span></span>  
 [<span data-ttu-id="66489-132">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="66489-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="66489-133">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="66489-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
