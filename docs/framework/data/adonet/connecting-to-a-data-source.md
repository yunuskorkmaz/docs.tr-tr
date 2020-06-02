---
title: Veri Kaynağına Bağlanma
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287083"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="b45d1-102">ADO.NET içinde bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="b45d1-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="b45d1-103">ADO.NET ' de, bir bağlantı dizesinde gerekli kimlik doğrulama bilgilerini sağlayarak belirli bir veri kaynağına bağlanmak için bir **bağlantı** nesnesi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b45d1-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="b45d1-104">Kullandığınız **bağlantı** nesnesi, veri kaynağının türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b45d1-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="b45d1-105">.NET Framework eklenen her bir .NET Framework veri sağlayıcısı bir nesnesine sahiptir <xref:System.Data.Common.DbConnection> : OLE DB için .NET Framework veri sağlayıcısı bir nesne içeriyorsa, .NET Framework için veri sağlayıcısı SQL Server bir nesne içerir, ODBC için .NET Framework veri sağlayıcısı bir nesnesi içerir <xref:System.Data.OleDb.OleDbConnection> <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.Odbc.OdbcConnection> ve Oracle için <xref:System.Data.OracleClient.OracleConnection> .NET Framework veri sağlayıcısı bir nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="b45d1-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b45d1-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b45d1-106">In This Section</span></span>  
 <span data-ttu-id="b45d1-107">[Bağlantı kuruluyor](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="b45d1-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="b45d1-108">Bir veri kaynağıyla bağlantı kurmak için bir **bağlantı** nesnesinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b45d1-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="b45d1-109">[Bağlantı olayları](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="b45d1-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="b45d1-110">Bir veri kaynağından bilgilendirici iletileri almak için bir **InfoMessage** olayının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b45d1-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45d1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b45d1-111">See also</span></span>

- [<span data-ttu-id="b45d1-112">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="b45d1-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="b45d1-113">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="b45d1-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="b45d1-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="b45d1-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b45d1-115">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="b45d1-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="b45d1-116">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="b45d1-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="b45d1-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b45d1-117">ADO.NET Overview</span></span>](ado-net-overview.md)
