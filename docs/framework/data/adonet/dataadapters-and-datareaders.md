---
title: DataAdapters ve DataReaders
description: Bir veritabanından veri alan ve veri kaynağından veri alan ve bir veri kümesini dolduran ADO.NET DataReader hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 2584f8b382dd90f2f8b4554663dc545b9ccceb62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177611"
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="42347-103">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="42347-103">DataAdapters and DataReaders</span></span>

<span data-ttu-id="42347-104">Bir veritabanından salt okunurdur ve salt ileri bir veri akışı almak için ADO.NET **DataReader** 'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42347-104">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="42347-105">Sonuçlar sorgu yürütüldüğü için döndürülür ve **DataReader**'ın **Read** yöntemini kullanarak isteene kadar istemcideki ağ arabelleğine depolanır.</span><span class="sxs-lookup"><span data-stu-id="42347-105">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="42347-106">**DataReader** 'ın kullanılması, hem verileri kullanılabilir duruma getirerek hem de (varsayılan olarak), bellekteki bir seferde yalnızca bir satır depolayarak sistem yükünü azaltarak uygulama performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="42347-106">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="42347-107">Bir <xref:System.Data.Common.DataAdapter> veri kaynağından veri almak ve içindeki tabloları doldurmak için kullanılır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="42347-107">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="42347-108">`DataAdapter`Ayrıca veri kaynağına geri yapılan değişiklikleri de çözer `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="42347-108">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="42347-109">, `DataAdapter` `Connection` Bir veri kaynağına bağlanmak için .NET Framework veri sağlayıcısının nesnesini kullanır ve veri `Command` kaynağındaki değişiklikleri almak ve verileri çözümlemek için nesneleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="42347-109">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="42347-110">.NET Framework eklenen her .NET Framework veri sağlayıcısının bir ve bir nesnesi vardır <xref:System.Data.Common.DbDataReader> <xref:System.Data.Common.DbDataAdapter> : OLE DB için .NET Framework veri sağlayıcısı bir ve nesnesi içeriyorsa, .NET Framework için veri sağlayıcısı SQL Server bir ve nesnesi Içerir ve <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.OleDb.OleDbDataAdapter> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataAdapter> <xref:System.Data.Odbc.OdbcDataReader> <xref:System.Data.Odbc.OdbcDataAdapter> Oracle için <xref:System.Data.OracleClient.OracleDataReader> <xref:System.Data.OracleClient.OracleDataAdapter> .NET Framework veri sağlayıcısı, ve bir nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="42347-110">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42347-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="42347-111">In This Section</span></span>  

 [<span data-ttu-id="42347-112">DataReader Kullanarak Veri Alma</span><span class="sxs-lookup"><span data-stu-id="42347-112">Retrieving Data Using a DataReader</span></span>](retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="42347-113">ADO.NET **DataReader** nesnesini ve bir veri kaynağından sonuçların akışını döndürmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="42347-113">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="42347-114">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="42347-114">Populating a DataSet from a DataAdapter</span></span>](populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="42347-115">' `DataSet` I kullanarak bir tablo, sütun ve satır ile nasıl doldurulacağını açıklar `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="42347-115">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="42347-116">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="42347-116">DataAdapter Parameters</span></span>](dataadapter-parameters.md)  
 <span data-ttu-id="42347-117">`DataAdapter`İçindeki bir sütunun içeriklerinin bir komut parametresine nasıl eşlenme dahil olmak üzere öğesinin komut özellikleriyle parametrelerin nasıl kullanılacağını açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="42347-117">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="42347-118">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="42347-118">Adding Existing Constraints to a DataSet</span></span>](adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="42347-119">' A varolan kısıtlamaların nasıl ekleneceğini açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="42347-119">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="42347-120">DataAdapter DataTable ve DataColumn Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="42347-120">DataAdapter DataTable and DataColumn Mappings</span></span>](dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="42347-121">' Nin nasıl ayarlanacağını açıklar `DataTableMappings` `ColumnMappings` `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="42347-121">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="42347-122">Sorgu Sonucunu Sayfalama</span><span class="sxs-lookup"><span data-stu-id="42347-122">Paging Through a Query Result</span></span>](paging-through-a-query-result.md)  
 <span data-ttu-id="42347-123">Sorgunun sonuçlarını veri sayfaları olarak görüntülemenin bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="42347-123">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="42347-124">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="42347-124">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="42347-125">`DataAdapter`Veritabanına geri yapılan değişiklikleri çözümlemek için ' nin nasıl kullanılacağını açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="42347-125">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="42347-126">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="42347-126">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)  
 <span data-ttu-id="42347-127">`DataAdapter`Olayları ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="42347-127">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="42347-128">DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="42347-128">Performing Batch Operations Using DataAdapters</span></span>](performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="42347-129">' Den Güncelleştirme uygulanırken SQL Server gidiş dönüş sayısını azaltarak uygulama performansının nasıl geliştirileneceğini açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="42347-129">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42347-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42347-130">See also</span></span>

- [<span data-ttu-id="42347-131">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="42347-131">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="42347-132">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="42347-132">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="42347-133">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="42347-133">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="42347-134">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="42347-134">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="42347-135">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="42347-135">ADO.NET Overview</span></span>](ado-net-overview.md)
