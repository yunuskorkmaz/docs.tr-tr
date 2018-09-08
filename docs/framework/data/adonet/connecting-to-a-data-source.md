---
title: ADO.NET'te veri kaynağına bağlanma
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: f5788b9b0b19f32d03c917575db7b3f40324c0a2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189270"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="b15c7-102">ADO.NET'te veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="b15c7-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="b15c7-103">ADO.NET kullandığınız bir **bağlantı** bağlantı dizesinde gerekli kimlik doğrulama bilgileri vererek belirli bir veri kaynağına bağlanmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b15c7-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="b15c7-104">**Bağlantı** kullandığınız nesne veri kaynağı türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="b15c7-105">.NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbConnection> nesne: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbConnection> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlConnection> nesnesi. ODBC için NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.Odbc.OdbcConnection> nesne ve Oracle için .NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.OracleClient.OracleConnection> nesne.</span><span class="sxs-lookup"><span data-stu-id="b15c7-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b15c7-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b15c7-106">In This Section</span></span>  
 [<span data-ttu-id="b15c7-107">Bağlantı Kurma</span><span class="sxs-lookup"><span data-stu-id="b15c7-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="b15c7-108">Nasıl kullanılacağını açıklayan bir **bağlantı** bir veri kaynağına bağlantı kurmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b15c7-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="b15c7-109">Bağlantı Olayları </span><span class="sxs-lookup"><span data-stu-id="b15c7-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="b15c7-110">Nasıl kullanılacağını açıklayan bir **InfoMessage** bir veri kaynağından bilgi iletilerini almak için olay.</span><span class="sxs-lookup"><span data-stu-id="b15c7-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15c7-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-111">See Also</span></span>  
 [<span data-ttu-id="b15c7-112">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="b15c7-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="b15c7-113">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="b15c7-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="b15c7-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="b15c7-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="b15c7-115">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="b15c7-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="b15c7-116">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="b15c7-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="b15c7-117">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b15c7-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
