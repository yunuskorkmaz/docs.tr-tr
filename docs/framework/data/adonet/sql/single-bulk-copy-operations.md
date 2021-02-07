---
description: 'Daha fazla bilgi edinin: tekli toplu kopyalama Işlemleri'
title: Tekil Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: f6b046fbd73ad798f3f9f117eea0b72f46e43b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767485"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="6f5ae-103">Tekil Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="6f5ae-103">Single Bulk Copy Operations</span></span>

<span data-ttu-id="6f5ae-104">SQL Server toplu kopyalama işlemi gerçekleştirmeye yönelik en basit yaklaşım, bir veritabanına karşı tek bir işlem gerçekleştirkullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-104">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="6f5ae-105">Varsayılan olarak, bir toplu kopyalama işlemi yalıtılmış bir işlem olarak gerçekleştirilir: kopyalama işlemi, geri alma için hiçbir fırsat olmadan, işlem temelli olmayan bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-105">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>

> [!NOTE]
> <span data-ttu-id="6f5ae-106">Bir hata oluştuğunda toplu kopyalama işleminin tamamını veya bir kısmını geri almanız gerekiyorsa, <xref:System.Data.SqlClient.SqlBulkCopy> yönetilen bir işlem kullanabilir ya da mevcut bir işlem içinde toplu kopyalama işlemini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-106">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="6f5ae-107"> Ayrıca, <xref:System.Transactions> bağlantı kayıtlı (örtük veya açık) bir **System. Transactions** hareketiyle birlikte, SqlBulkCopy ile de çalışacaksınız.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-107">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>
>
> <span data-ttu-id="6f5ae-108">Daha fazla bilgi için bkz. [işlem ve toplu kopyalama işlemleri](transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6f5ae-108">For more information, see [Transaction and Bulk Copy Operations](transaction-and-bulk-copy-operations.md).</span></span>

<span data-ttu-id="6f5ae-109">Toplu kopyalama işlemi gerçekleştirmeye yönelik genel adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6f5ae-109">The general steps for performing a bulk copy operation are as follows:</span></span>

1. <span data-ttu-id="6f5ae-110">Kaynak sunucuya bağlanın ve kopyalanacak verileri alın.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-110">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="6f5ae-111">Veriler bir veya nesnesinden alınalınabilmesi için diğer kaynaklardan da gelebilir <xref:System.Data.IDataReader> <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="6f5ae-111">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>

2. <span data-ttu-id="6f5ae-112">Hedef sunucuya bağlanın ( **SqlBulkCopy** 'ın sizin için bir bağlantı kurmasını istemediğiniz müddetçe).</span><span class="sxs-lookup"><span data-stu-id="6f5ae-112">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>

3. <span data-ttu-id="6f5ae-113"><xref:System.Data.SqlClient.SqlBulkCopy>Gerekli özellikleri ayarlayarak bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-113">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>

4. <span data-ttu-id="6f5ae-114">Toplu ekleme işlemi için hedef tabloyu göstermek üzere **DestinationTableName** özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-114">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>

5. <span data-ttu-id="6f5ae-115">**WriteToServer** yöntemlerinden birini çağırın.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-115">Call one of the **WriteToServer** methods.</span></span>

6. <span data-ttu-id="6f5ae-116">İsteğe bağlı olarak, özellikleri güncelleştirin ve gerekirse **WriteToServer** ' ı çağırın.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-116">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>

7. <span data-ttu-id="6f5ae-117"><xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>Bir bildirimde toplu kopyalama işlemlerini çağırın veya sarın `Using` .</span><span class="sxs-lookup"><span data-stu-id="6f5ae-117">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>

> [!CAUTION]
> <span data-ttu-id="6f5ae-118">Kaynak ve hedef sütun veri türlerinin eşleşmesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-118">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="6f5ae-119">Veri türleri eşleşmiyorsa, **SqlBulkCopy** , tarafından kullanılan kuralları kullanarak her bir kaynak değeri hedef veri türüne dönüştürmeye çalışır <xref:System.Data.SqlClient.SqlParameter.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f5ae-119">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="6f5ae-120">Dönüşümler performansı etkileyebilir ve ayrıca beklenmeyen hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-120">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="6f5ae-121">Örneğin, bir `Double` veri türü `Decimal` çoğu zaman bir veri türüne dönüştürülebilir, ancak her zaman değildir.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-121">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>

## <a name="example"></a><span data-ttu-id="6f5ae-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f5ae-122">Example</span></span>

<span data-ttu-id="6f5ae-123">Aşağıdaki konsol uygulaması, sınıfını kullanarak nasıl veri yükleneceğini gösterir <xref:System.Data.SqlClient.SqlBulkCopy> .</span><span class="sxs-lookup"><span data-stu-id="6f5ae-123">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="6f5ae-124">Bu örnekte, <xref:System.Data.SqlClient.SqlDataReader> SQL Server **AdventureWorks** veritabanındaki **Production. Product** tablosundan aynı veritabanındaki benzer bir tabloya veri kopyalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-124">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f5ae-125">Bu örnek, [toplu kopyalama örnek kurulumu](bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-125">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="6f5ae-126">Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-126">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="6f5ae-127">Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .</span><span class="sxs-lookup"><span data-stu-id="6f5ae-127">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="6f5ae-128">Transact-SQL ve komut sınıfını kullanarak toplu kopyalama Işlemi gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6f5ae-128">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>

<span data-ttu-id="6f5ae-129">Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> bulk INSERT ifadesini yürütmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-129">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>

> [!NOTE]
> <span data-ttu-id="6f5ae-130">Veri kaynağı için dosya yolu sunucuya göredir.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-130">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="6f5ae-131">Toplu kopyalama işleminin başarılı olabilmesi için sunucu işleminin bu yola erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-131">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6f5ae-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f5ae-132">See also</span></span>

- [<span data-ttu-id="6f5ae-133">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="6f5ae-133">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="6f5ae-134">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f5ae-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
