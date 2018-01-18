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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1df18730d3a4428f245fe4222dafec0eaf6c08a5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="b7199-102">ADO.NET veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="b7199-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="b7199-103">ADO.NET kullandığınız bir **bağlantı** bağlantı dizesinde gerekli kimlik doğrulama bilgileri sağlayarak bir özel veri kaynağına bağlanmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b7199-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="b7199-104">**Bağlantı** kullandığınız nesne veri kaynağı türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7199-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="b7199-105">.NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbConnection> nesnesi: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbConnection> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlConnection> nesnesi. NET Framework veri sağlayıcısı için ODBC içeren bir <xref:System.Data.Odbc.OdbcConnection> nesne ve Oracle için .NET Framework veri sağlayıcısı içeren bir <xref:System.Data.OracleClient.OracleConnection> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b7199-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7199-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b7199-106">In This Section</span></span>  
 [<span data-ttu-id="b7199-107">Bağlantı Kurma</span><span class="sxs-lookup"><span data-stu-id="b7199-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="b7199-108">Nasıl kullanılacağını açıklar bir **bağlantı** bir veri kaynağı bağlantı kurmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b7199-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="b7199-109">Bağlantı Olayları </span><span class="sxs-lookup"><span data-stu-id="b7199-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="b7199-110">Nasıl kullanılacağını açıklar bir **InfoMessage** bilgilendirici iletileri bir veri kaynağından veri almak için olay.</span><span class="sxs-lookup"><span data-stu-id="b7199-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7199-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7199-111">See Also</span></span>  
 [<span data-ttu-id="b7199-112">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="b7199-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="b7199-113">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="b7199-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="b7199-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7199-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="b7199-115">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="b7199-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="b7199-116">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="b7199-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="b7199-117">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b7199-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
