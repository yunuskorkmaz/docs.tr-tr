---
title: Veri Kaynağına Bağlanma
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: b9e69b029ad37c583e51c219f87ff9d7d8e7315c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203780"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="5f125-102">ADO.NET içinde bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="5f125-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="5f125-103">ADO.NET ' de, bir bağlantı dizesinde gerekli kimlik doğrulama bilgilerini sağlayarak belirli bir veri kaynağına bağlanmak için bir **bağlantı** nesnesi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5f125-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="5f125-104">Kullandığınız **bağlantı** nesnesi, veri kaynağının türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5f125-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="5f125-105">.NET Framework eklenen her bir .NET Framework veri sağlayıcısı bir nesnesine sahiptir <xref:System.Data.Common.DbConnection> : OLE DB için .NET Framework veri sağlayıcısı bir nesne içeriyorsa, .NET Framework için veri sağlayıcısı SQL Server bir nesne içerir, ODBC için .NET Framework veri sağlayıcısı bir nesnesi içerir <xref:System.Data.OleDb.OleDbConnection> <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.Odbc.OdbcConnection> ve Oracle için <xref:System.Data.OracleClient.OracleConnection> .NET Framework veri sağlayıcısı bir nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5f125-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f125-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5f125-106">In This Section</span></span>  

 <span data-ttu-id="5f125-107">[Bağlantı kuruluyor](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="5f125-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="5f125-108">Bir veri kaynağıyla bağlantı kurmak için bir **bağlantı** nesnesinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5f125-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="5f125-109">[Bağlantı olayları](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="5f125-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="5f125-110">Bir veri kaynağından bilgilendirici iletileri almak için bir **InfoMessage** olayının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5f125-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f125-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f125-111">See also</span></span>

- [<span data-ttu-id="5f125-112">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="5f125-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="5f125-113">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="5f125-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="5f125-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f125-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="5f125-115">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="5f125-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="5f125-116">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="5f125-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="5f125-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5f125-117">ADO.NET Overview</span></span>](ado-net-overview.md)
