---
title: "Bir komutu yürütme"
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
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c4879c49a410dfb40999f3163d8b23158cb71f0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="executing-a-command"></a><span data-ttu-id="b280b-102">Bir komutu yürütme</span><span class="sxs-lookup"><span data-stu-id="b280b-102">Executing a Command</span></span>
<span data-ttu-id="b280b-103">.NET Framework ile dahil her .NET Framework veri sağlayıcısı devraldığı kendi komut nesnesi sahip <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="b280b-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="b280b-104">OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbCommand> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlCommand> nesne ODBC için .NET Framework veri sağlayıcısı içeren bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcı içeren bir <xref:System.Data.OracleClient.OracleCommand> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b280b-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="b280b-105">Komutlar yürütülürken bu nesneleri çıkarır yöntemlerin her biri komut türüne göre ve dönüş değeri, aşağıdaki tabloda açıklandığı gibi istenen.</span><span class="sxs-lookup"><span data-stu-id="b280b-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="b280b-106">Komut</span><span class="sxs-lookup"><span data-stu-id="b280b-106">Command</span></span>|<span data-ttu-id="b280b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b280b-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="b280b-108">Döndürür bir `DataReader` nesne.</span><span class="sxs-lookup"><span data-stu-id="b280b-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="b280b-109">Tek bir sayı değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b280b-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="b280b-110">Herhangi bir satır döndürmeyen bir komut yürütür.</span><span class="sxs-lookup"><span data-stu-id="b280b-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="b280b-111">Döndürür bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b280b-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b280b-112">İçin kullanılabilir bir `SqlCommand` yalnızca nesne.</span><span class="sxs-lookup"><span data-stu-id="b280b-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="b280b-113">Her kesin türü belirtilmiş komut nesnesi de destekleyen bir <xref:System.Data.CommandType> belirten bir komut dizesi nasıl yorumlanacağını, aşağıdaki tabloda açıklandığı gibi numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b280b-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="b280b-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="b280b-114">CommandType</span></span>|<span data-ttu-id="b280b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b280b-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="b280b-116">Veri kaynağında yürütülecek deyimleri tanımlayan bir SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="b280b-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="b280b-117">Saklı yordam adı.</span><span class="sxs-lookup"><span data-stu-id="b280b-117">The name of the stored procedure.</span></span> <span data-ttu-id="b280b-118">Kullanabileceğiniz `Parameters` giriş ve çıkış parametreleri erişme ve dönüş değerleri, bağımsız olarak bir komut özelliğinin `Execute` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b280b-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="b280b-119">Kullanırken `ExecuteReader`, dönüş değerleri ve çıktı parametreleri kadar erişilemeyecek `DataReader` kapalı.</span><span class="sxs-lookup"><span data-stu-id="b280b-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="b280b-120">Bir tablonun adı.</span><span class="sxs-lookup"><span data-stu-id="b280b-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b280b-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b280b-121">Example</span></span>  
 <span data-ttu-id="b280b-122">Aşağıdaki kod örneğinde nasıl oluşturulduğunu gösteren bir <xref:System.Data.SqlClient.SqlCommand> özelliklerini ayarlayarak bir saklı yordamı yürütmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="b280b-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="b280b-123">A <xref:System.Data.SqlClient.SqlParameter> nesne saklı yordamı için giriş parametresi belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b280b-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="b280b-124">Komutu kullanılarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi ve çıktısını <xref:System.Data.SqlClient.SqlDataReader> konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b280b-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="b280b-125">Sorun giderme komutları</span><span class="sxs-lookup"><span data-stu-id="b280b-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="b280b-126">SQL Server için .NET Framework veri sağlayıcısı başarısız komutu yürütmeleri için zaman zaman ortaya çıkan sorunları algılamak etkinleştirmek için performans sayaçlarını ekler.</span><span class="sxs-lookup"><span data-stu-id="b280b-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="b280b-127">Daha fazla bilgi için bkz: [performans sayaçları](../../../../docs/framework/data/adonet/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="b280b-127">For more information see [Performance Counters](../../../../docs/framework/data/adonet/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b280b-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b280b-128">See Also</span></span>  
 [<span data-ttu-id="b280b-129">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="b280b-129">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="b280b-130">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="b280b-130">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="b280b-131">DataReader ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b280b-131">Working with DataReaders</span></span>](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="b280b-132">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b280b-132">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
