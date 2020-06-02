---
title: Bağlantı Havuzu
description: ADO.NET 'in veri kaynaklarına bağlantıların açılış maliyetini en aza indirmek için kullandığı bir iyileştirme teknii olan bağlantı havuzu hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: b8f89dfda7edbde14dbb5945f10f2284ac43c3d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287096"
---
# <a name="connection-pooling"></a><span data-ttu-id="7fb56-103">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="7fb56-103">Connection Pooling</span></span>
<span data-ttu-id="7fb56-104">Bir veri kaynağına bağlanmak zaman alıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fb56-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="7fb56-105">ADO.NET bağlantıları açma maliyetini en aza indirmek için, *bağlantı havuzu*adlı bir iyileştirme tekniği kullanır, bu da bağlantıları tekrar tekrar açan ve kapatan maliyeti azaltır.</span><span class="sxs-lookup"><span data-stu-id="7fb56-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="7fb56-106">Bağlantı havuzu .NET Framework veri sağlayıcıları için farklı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="7fb56-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7fb56-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7fb56-107">In This Section</span></span>  
 [<span data-ttu-id="7fb56-108">SQL Server Bağlantı Havuzu (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="7fb56-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="7fb56-109">Bağlantı havuza genel bir bakış sağlar ve bağlantı havuzunun SQL Server nasıl çalıştığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7fb56-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="7fb56-110">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="7fb56-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="7fb56-111">OLE DB için .NET Framework Veri Sağlayıcısı, ODBC için .NET Framework Veri Sağlayıcısı ve Oracle için .NET Framework veri sağlayıcısı için bağlantı havuzu oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7fb56-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb56-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fb56-112">See also</span></span>

- [<span data-ttu-id="7fb56-113">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7fb56-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="7fb56-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7fb56-114">ADO.NET Overview</span></span>](ado-net-overview.md)
