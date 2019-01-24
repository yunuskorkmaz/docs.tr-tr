---
title: ADO.NET'te veri kaynağına bağlanma
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 20cf22e1c9b9bf18dd3109cb9589c05a6c27d4d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701748"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="27ac0-102">ADO.NET'te veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="27ac0-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="27ac0-103">ADO.NET kullandığınız bir **bağlantı** bağlantı dizesinde gerekli kimlik doğrulama bilgileri vererek belirli bir veri kaynağına bağlanmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="27ac0-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="27ac0-104">**Bağlantı** kullandığınız nesne veri kaynağı türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="27ac0-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="27ac0-105">.NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbConnection> nesne: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbConnection> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlConnection> nesnesi. ODBC için NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.Odbc.OdbcConnection> nesne ve Oracle için .NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.OracleClient.OracleConnection> nesne.</span><span class="sxs-lookup"><span data-stu-id="27ac0-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27ac0-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="27ac0-106">In This Section</span></span>  
 [<span data-ttu-id="27ac0-107">Bağlantı Kurma</span><span class="sxs-lookup"><span data-stu-id="27ac0-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="27ac0-108">Nasıl kullanılacağını açıklayan bir **bağlantı** bir veri kaynağına bağlantı kurmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="27ac0-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="27ac0-109">Bağlantı Olayları </span><span class="sxs-lookup"><span data-stu-id="27ac0-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="27ac0-110">Nasıl kullanılacağını açıklayan bir **InfoMessage** bir veri kaynağından bilgi iletilerini almak için olay.</span><span class="sxs-lookup"><span data-stu-id="27ac0-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ac0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27ac0-111">See also</span></span>
- [<span data-ttu-id="27ac0-112">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="27ac0-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="27ac0-113">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="27ac0-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)
- [<span data-ttu-id="27ac0-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="27ac0-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="27ac0-115">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="27ac0-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="27ac0-116">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="27ac0-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="27ac0-117">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="27ac0-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
