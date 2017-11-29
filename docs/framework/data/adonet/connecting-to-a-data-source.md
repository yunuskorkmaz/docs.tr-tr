---
title: "ADO.NET veri kaynağına bağlanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0d21c571b659e9d7aef65893db18b034d614e2af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="43028-102">ADO.NET veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="43028-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="43028-103">ADO.NET kullandığınız bir **bağlantı** bağlantı dizesinde gerekli kimlik doğrulama bilgileri sağlayarak bir özel veri kaynağına bağlanmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="43028-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="43028-104">**Bağlantı** kullandığınız nesne veri kaynağı türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="43028-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="43028-105">.NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbConnection> nesnesi: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbConnection> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlConnection> nesnesi. NET Framework veri sağlayıcısı için ODBC içeren bir <xref:System.Data.Odbc.OdbcConnection> nesne ve Oracle için .NET Framework veri sağlayıcısı içeren bir <xref:System.Data.OracleClient.OracleConnection> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43028-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43028-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="43028-106">In This Section</span></span>  
 [<span data-ttu-id="43028-107">Bağlantı oluşturma</span><span class="sxs-lookup"><span data-stu-id="43028-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="43028-108">Nasıl kullanılacağını açıklar bir **bağlantı** bir veri kaynağı bağlantı kurmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="43028-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="43028-109">Bağlantı olayları</span><span class="sxs-lookup"><span data-stu-id="43028-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="43028-110">Nasıl kullanılacağını açıklar bir **InfoMessage** bilgilendirici iletileri bir veri kaynağından veri almak için olay.</span><span class="sxs-lookup"><span data-stu-id="43028-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43028-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43028-111">See Also</span></span>  
 [<span data-ttu-id="43028-112">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="43028-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="43028-113">Bağlantı havuzu</span><span class="sxs-lookup"><span data-stu-id="43028-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="43028-114">Komutları ve parametreleri</span><span class="sxs-lookup"><span data-stu-id="43028-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="43028-115">DataAdapters ve DataReader</span><span class="sxs-lookup"><span data-stu-id="43028-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="43028-116">İşlemler ve eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="43028-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="43028-117">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="43028-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
