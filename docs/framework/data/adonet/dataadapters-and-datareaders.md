---
title: DataAdapters ve DataReader
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e7a0af0b5fabdfacfcc825258242868b0fbb513
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="60d4b-102">DataAdapters ve DataReader</span><span class="sxs-lookup"><span data-stu-id="60d4b-102">DataAdapters and DataReaders</span></span>
<span data-ttu-id="60d4b-103">ADO.NET kullanabilirsiniz **DataReader** bir veritabanından veri salt okunur, yalnızca ileri akışı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="60d4b-103">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="60d4b-104">Sonuçları sorgu yürütür ve bunları isteyen kadar istemci üzerinde ağ arabelleği depolanan gibi döndürülür kullanarak **okuma** yöntemi **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="60d4b-104">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="60d4b-105">Kullanarak **DataReader** hem kullanılabilir olduğunda hemen verileri alarak ve (varsayılan) uygulama performansını artırabilirsiniz sistem yükünü azaltma bellekte bir anda yalnızca bir satır depolama.</span><span class="sxs-lookup"><span data-stu-id="60d4b-105">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="60d4b-106">A <xref:System.Data.Common.DataAdapter> bir veri kaynağından veri almak ve tablolarına doldurmak için kullanılan bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="60d4b-106">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="60d4b-107">`DataAdapter` Yapılan değişiklikleri de çözümler `DataSet` veri kaynağına geri.</span><span class="sxs-lookup"><span data-stu-id="60d4b-107">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="60d4b-108">`DataAdapter` Kullanan `Connection` nesne bir veri kaynağı ve onu bağlanmak için .NET Framework Veri Sağlayıcısı'nın kullandığı `Command` verilerin alınacağı ve veri kaynağına değişiklikler çözümlemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="60d4b-108">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="60d4b-109">.NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbDataReader> ve <xref:System.Data.Common.DbDataAdapter> nesnesi: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbDataReader> ve bir <xref:System.Data.OleDb.OleDbDataAdapter> nesnesi, SQL için .NET Framework veri sağlayıcısı Sunucuyu içeren bir <xref:System.Data.SqlClient.SqlDataReader> ve <xref:System.Data.SqlClient.SqlDataAdapter> nesne ODBC için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.Odbc.OdbcDataReader> ve bir <xref:System.Data.Odbc.OdbcDataAdapter> nesne ve Oracle için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OracleClient.OracleDataReader> ve bir <xref:System.Data.OracleClient.OracleDataAdapter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="60d4b-109">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60d4b-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="60d4b-110">In This Section</span></span>  
 [<span data-ttu-id="60d4b-111">DataReader kullanarak veri alma</span><span class="sxs-lookup"><span data-stu-id="60d4b-111">Retrieving Data Using a DataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="60d4b-112">ADO.NET açıklar **DataReader** nesne ve nasıl sonuçlarının bir akış veri kaynağından döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60d4b-112">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="60d4b-113">DataAdapter kümesinden doldurma</span><span class="sxs-lookup"><span data-stu-id="60d4b-113">Populating a DataSet from a DataAdapter</span></span>](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="60d4b-114">Doldurmak nasıl açıklar bir `DataSet` tabloları, sütunları ve satırları kullanarak bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="60d4b-114">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="60d4b-115">DataAdapter parametreleri</span><span class="sxs-lookup"><span data-stu-id="60d4b-115">DataAdapter Parameters</span></span>](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 <span data-ttu-id="60d4b-116">Parametreler ile komut özelliklerini kullanmayı açıklar bir `DataAdapter` bir sütunun içeriğine eşleme de dahil olmak üzere bir `DataSet` için bir komut parametresi.</span><span class="sxs-lookup"><span data-stu-id="60d4b-116">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="60d4b-117">Varolan kısıtlamaları bir veri kümesine ekleme</span><span class="sxs-lookup"><span data-stu-id="60d4b-117">Adding Existing Constraints to a DataSet</span></span>](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="60d4b-118">Varolan kısıtlamalara eklemeyi açıklar bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="60d4b-118">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="60d4b-119">DataAdapter DataTable ve DataColumn eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="60d4b-119">DataAdapter DataTable and DataColumn Mappings</span></span>](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="60d4b-120">Nasıl ayarlanacağını açıklar `DataTableMappings` ve `ColumnMappings` için bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="60d4b-120">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="60d4b-121">Sorgu sonucu disk belleği</span><span class="sxs-lookup"><span data-stu-id="60d4b-121">Paging Through a Query Result</span></span>](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 <span data-ttu-id="60d4b-122">Bir sorgunun sonuçlarını veri sayfaları olarak görüntüleme ilişkin bir örnek verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="60d4b-122">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="60d4b-123">Veri kaynakları ile DataAdapters güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="60d4b-123">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="60d4b-124">Nasıl kullanılacağını açıklar bir `DataAdapter` değişiklikleri çözümlemek için bir `DataSet` veritabanına.</span><span class="sxs-lookup"><span data-stu-id="60d4b-124">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="60d4b-125">Olaylarını işleme</span><span class="sxs-lookup"><span data-stu-id="60d4b-125">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 <span data-ttu-id="60d4b-126">Açıklar `DataAdapter` olaylar ve bunları nasıl kullanacağınızı.</span><span class="sxs-lookup"><span data-stu-id="60d4b-126">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="60d4b-127">DataAdapters kullanarak toplu işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="60d4b-127">Performing Batch Operations Using DataAdapters</span></span>](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="60d4b-128">Güncelleştirmeleri uygularken SQL Server'a gidiş dönüş sayısını azaltarak geliştirerek uygulama performansı açıklar `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="60d4b-128">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d4b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60d4b-129">See Also</span></span>  
 [<span data-ttu-id="60d4b-130">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="60d4b-130">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="60d4b-131">Komutları ve parametreleri</span><span class="sxs-lookup"><span data-stu-id="60d4b-131">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="60d4b-132">İşlemler ve eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="60d4b-132">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="60d4b-133">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="60d4b-133">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="60d4b-134">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="60d4b-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
