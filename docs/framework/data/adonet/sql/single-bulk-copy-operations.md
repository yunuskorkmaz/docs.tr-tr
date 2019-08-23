---
title: Tekil Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 8cba2201bf8087633103efe45c5236cab3af0a0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964748"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="dc405-102">Tekil Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dc405-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="dc405-103">SQL Server toplu kopyalama işlemi gerçekleştirmeye yönelik en basit yaklaşım, bir veritabanına karşı tek bir işlem gerçekleştirkullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="dc405-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="dc405-104">Varsayılan olarak, bir toplu kopyalama işlemi yalıtılmış bir işlem olarak gerçekleştirilir: kopyalama işlemi, geri alma için hiçbir fırsat olmadan, işlem temelli olmayan bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="dc405-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc405-105">Bir hata oluştuğunda toplu kopyalama işleminin tamamını veya bir kısmını geri almanız gerekiyorsa, yönetilen bir <xref:System.Data.SqlClient.SqlBulkCopy>işlem kullanabilir ya da mevcut bir işlem içinde toplu kopyalama işlemini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc405-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="dc405-106">Ayrıca, bağlantı kayıtlı (örtük <xref:System.Transactions> veya açık) bir **System. Transactions** hareketiyle birlikte, **SqlBulkCopy** ile de çalışacaksınız.</span><span class="sxs-lookup"><span data-stu-id="dc405-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="dc405-107">Daha fazla bilgi için bkz. [işlem ve toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="dc405-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="dc405-108">Toplu kopyalama işlemi gerçekleştirmeye yönelik genel adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dc405-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1. <span data-ttu-id="dc405-109">Kaynak sunucuya bağlanın ve kopyalanacak verileri alın.</span><span class="sxs-lookup"><span data-stu-id="dc405-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="dc405-110">Veriler bir <xref:System.Data.IDataReader> veya <xref:System.Data.DataTable> nesnesinden alınalınabilmesi için diğer kaynaklardan da gelebilir.</span><span class="sxs-lookup"><span data-stu-id="dc405-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2. <span data-ttu-id="dc405-111">Hedef sunucuya bağlanın ( **SqlBulkCopy** 'ın sizin için bir bağlantı kurmasını istemediğiniz müddetçe).</span><span class="sxs-lookup"><span data-stu-id="dc405-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3. <span data-ttu-id="dc405-112">Gerekli özellikleri <xref:System.Data.SqlClient.SqlBulkCopy> ayarlayarak bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc405-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4. <span data-ttu-id="dc405-113">Toplu ekleme işlemi için hedef tabloyu göstermek üzere **DestinationTableName** özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc405-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5. <span data-ttu-id="dc405-114">**WriteToServer** yöntemlerinden birini çağırın.</span><span class="sxs-lookup"><span data-stu-id="dc405-114">Call one of the **WriteToServer** methods.</span></span>  
  
6. <span data-ttu-id="dc405-115">İsteğe bağlı olarak, özellikleri güncelleştirin ve gerekirse **WriteToServer** ' ı çağırın.</span><span class="sxs-lookup"><span data-stu-id="dc405-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7. <span data-ttu-id="dc405-116"><xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> Bir`Using` bildirimde toplu kopyalama işlemlerini çağırın veya sarın.</span><span class="sxs-lookup"><span data-stu-id="dc405-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="dc405-117">Kaynak ve hedef sütun veri türlerinin eşleşmesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="dc405-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="dc405-118">Veri türleri eşleşmiyorsa, **SqlBulkCopy** , tarafından <xref:System.Data.SqlClient.SqlParameter.Value%2A>kullanılan kuralları kullanarak her bir kaynak değeri hedef veri türüne dönüştürmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="dc405-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="dc405-119">Dönüşümler performansı etkileyebilir ve ayrıca beklenmeyen hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc405-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="dc405-120">Örneğin, bir `Double` veri türü çoğu zaman bir `Decimal` veri türüne dönüştürülebilir, ancak her zaman değildir.</span><span class="sxs-lookup"><span data-stu-id="dc405-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc405-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc405-121">Example</span></span>  
 <span data-ttu-id="dc405-122">Aşağıdaki konsol uygulaması, <xref:System.Data.SqlClient.SqlBulkCopy> sınıfını kullanarak nasıl veri yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc405-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="dc405-123">Bu örnekte, <xref:System.Data.SqlClient.SqlDataReader> SQL Server **AdventureWorks** veritabanındaki **Production. Product** tablosundan aynı veritabanındaki benzer bir tabloya veri kopyalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc405-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dc405-124">Bu örnek, [toplu kopyalama örnek kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="dc405-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="dc405-125">Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc405-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="dc405-126">Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL `INSERT … SELECT` ifadesinin kullanılması daha kolay ve hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc405-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="dc405-127">Transact-SQL ve komut sınıfını kullanarak toplu kopyalama Işlemi gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="dc405-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="dc405-128">Aşağıdaki örnek, bulk INSERT ifadesini yürütmek için <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc405-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc405-129">Veri kaynağı için dosya yolu sunucuya göredir.</span><span class="sxs-lookup"><span data-stu-id="dc405-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="dc405-130">Toplu kopyalama işleminin başarılı olabilmesi için sunucu işleminin bu yola erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc405-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc405-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc405-131">See also</span></span>

- [<span data-ttu-id="dc405-132">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dc405-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="dc405-133">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="dc405-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
