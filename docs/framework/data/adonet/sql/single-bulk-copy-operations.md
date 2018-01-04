---
title: "Tek toplu kopyalama işlemleri"
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
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 03b255f92ed7123c14116e148f23571d21561bfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="562ef-102">Tek toplu kopyalama işlemleri</span><span class="sxs-lookup"><span data-stu-id="562ef-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="562ef-103">Bir SQL Server toplu kopyalama işlemi gerçekleştirmenin en kolay yaklaşım, tek bir işlemde bir veritabanında gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="562ef-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="562ef-104">Varsayılan olarak, yalıtılmış bir işlem olarak bir toplu kopyalama işlemi gerçekleştirilir: Bu çalışırken için fırsat ile geri işlem temelli olmayan bir şekilde, kopyalama işlemi gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="562ef-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="562ef-105">Hata oluştuğunda toplu kopyalama bölümünü veya tümünü geri almak gerekiyorsa, kullanabilir bir <xref:System.Data.SqlClient.SqlBulkCopy>-yönetilen işlem ya da var olan bir işlem içinde toplu kopyalama işlemi.</span><span class="sxs-lookup"><span data-stu-id="562ef-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="562ef-106">**SqlBulkCopy** birlikte çalışacağı <xref:System.Transactions> bağlantı (örtük veya açık olarak) içine kayıtlı değilse bir **System.Transactions** işlem.</span><span class="sxs-lookup"><span data-stu-id="562ef-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="562ef-107">Daha fazla bilgi için bkz: [işlem ve toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="562ef-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="562ef-108">Bir toplu kopyalama işlemi gerçekleştirmeye yönelik genel adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="562ef-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1.  <span data-ttu-id="562ef-109">Kaynak sunucuya bağlanın ve kopyalanacak veri alın.</span><span class="sxs-lookup"><span data-stu-id="562ef-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="562ef-110">Veri da gelebilir diğer kaynaklardan penceresinden alınabilir, bir <xref:System.Data.IDataReader> veya <xref:System.Data.DataTable> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="562ef-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2.  <span data-ttu-id="562ef-111">Hedef sunucuya (istediğiniz sürece **SqlBulkCopy** sizin için bir bağlantı kurmak için).</span><span class="sxs-lookup"><span data-stu-id="562ef-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3.  <span data-ttu-id="562ef-112">Oluşturma bir <xref:System.Data.SqlClient.SqlBulkCopy> nesnesi, tüm gerekli özellikleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="562ef-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4.  <span data-ttu-id="562ef-113">Ayarlama **DestinationTableName** toplu için hedef tablo belirtmek için özellik ekleme işlemi.</span><span class="sxs-lookup"><span data-stu-id="562ef-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5.  <span data-ttu-id="562ef-114">Birini çağırın **WriteToServer** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="562ef-114">Call one of the **WriteToServer** methods.</span></span>  
  
6.  <span data-ttu-id="562ef-115">İsteğe bağlı olarak, güncelleştirme özellikleri ve çağrı **WriteToServer** yeniden gerektiği.</span><span class="sxs-lookup"><span data-stu-id="562ef-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7.  <span data-ttu-id="562ef-116">Çağrı <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, veya toplu kopyalama işlemleri içinde kaydırma bir `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="562ef-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="562ef-117">Kaynak ve hedef sütun veri türleri eşleşmesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="562ef-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="562ef-118">Veri türleri eşleşmiyorsa **SqlBulkCopy** her kaynak değeri tarafından işe kurallarını kullanarak hedef veri türüne dönüştürmek çalışır <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="562ef-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="562ef-119">Dönüşümler performansını etkileyebilir ve ayrıca beklenmeyen hatalara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="562ef-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="562ef-120">Örneğin, bir `Double` veri türüne dönüştürülebilir bir `Decimal` veri türü çoğu zaman, ancak her zaman.</span><span class="sxs-lookup"><span data-stu-id="562ef-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="562ef-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="562ef-121">Example</span></span>  
 <span data-ttu-id="562ef-122">Aşağıdaki konsol uygulaması kullanarak veri yüklemek gösterilmiştir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="562ef-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="562ef-123">Bu örnekte, bir <xref:System.Data.SqlClient.SqlDataReader> veri kopyalamak için kullanılan **Production.Product** tablosundaki [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] **AdventureWorks** benzer bir tabloya aynı veritabanında veritabanı.</span><span class="sxs-lookup"><span data-stu-id="562ef-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]**AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="562ef-124">Bölümünde açıklandığı gibi iş tabloları oluşturmadıysanız Bu örnek çalışmaz [toplu kopyalama örnek Kurulum](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="562ef-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="562ef-125">Bu kodu kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca.</span><span class="sxs-lookup"><span data-stu-id="562ef-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="562ef-126">Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="562ef-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="562ef-127">Transact-SQL ve komut sınıfı kullanılarak bir toplu kopyalama işlemi gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="562ef-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="562ef-128">Aşağıdaki örnekte nasıl kullanılacağını anlatan <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntemi BULK INSERT deyimini yürütün.</span><span class="sxs-lookup"><span data-stu-id="562ef-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="562ef-129">Veri kaynağı için dosya yolu göreli sunucudur.</span><span class="sxs-lookup"><span data-stu-id="562ef-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="562ef-130">Sunucu işlemi sırada toplu kopyalama işleminin başarılı olması bu yola erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="562ef-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="562ef-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="562ef-131">See Also</span></span>  
 [<span data-ttu-id="562ef-132">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="562ef-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="562ef-133">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="562ef-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
