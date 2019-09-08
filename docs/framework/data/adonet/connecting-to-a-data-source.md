---
title: ADO.NET içinde bir veri kaynağına bağlanma
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786769"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="1e839-102">ADO.NET içinde bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="1e839-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="1e839-103">ADO.NET ' de, bir bağlantı dizesinde gerekli kimlik doğrulama bilgilerini sağlayarak belirli bir veri kaynağına bağlanmak için bir **bağlantı** nesnesi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1e839-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="1e839-104">Kullandığınız **bağlantı** nesnesi, veri kaynağının türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e839-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="1e839-105">.NET Framework eklenen her .NET Framework veri sağlayıcısı bir <xref:System.Data.Common.DbConnection> nesnesine sahiptir: OLE DB için .NET Framework veri sağlayıcısı bir nesne <xref:System.Data.OleDb.OleDbConnection> içeriyorsa, .NET Framework veri sağlayıcısı SQL Server bir <xref:System.Data.SqlClient.SqlConnection> nesnesi içerir. ODBC için net Framework veri sağlayıcısı bir <xref:System.Data.Odbc.OdbcConnection> nesne içerir ve Oracle için .NET Framework veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleConnection> nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="1e839-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e839-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1e839-106">In This Section</span></span>  
 [<span data-ttu-id="1e839-107">Bağlantı Kurma</span><span class="sxs-lookup"><span data-stu-id="1e839-107">Establishing the Connection</span></span>](establishing-the-connection.md)  
 <span data-ttu-id="1e839-108">Bir veri kaynağıyla bağlantı kurmak için bir **bağlantı** nesnesinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1e839-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="1e839-109">Bağlantı Olayları </span><span class="sxs-lookup"><span data-stu-id="1e839-109">Connection Events</span></span>](connection-events.md)  
 <span data-ttu-id="1e839-110">Bir veri kaynağından bilgilendirici iletileri almak için bir **InfoMessage** olayının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1e839-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e839-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e839-111">See also</span></span>

- [<span data-ttu-id="1e839-112">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="1e839-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="1e839-113">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="1e839-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="1e839-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e839-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="1e839-115">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="1e839-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="1e839-116">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="1e839-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="1e839-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1e839-117">ADO.NET Overview</span></span>](ado-net-overview.md)
