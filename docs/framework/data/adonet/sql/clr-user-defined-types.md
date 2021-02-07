---
description: 'Daha fazla bilgi edinin: CLR User-Defined türleri'
title: Kullanıcı Tanımlı CLR Türleri
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: f1732c254d3bf3cb8aa4ba727c420c46ef55c2cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663371"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="23475-103">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="23475-103">CLR User-Defined Types</span></span>

<span data-ttu-id="23475-104">Microsoft SQL Server, Microsoft .NET Framework ortak dil çalışma zamanı (CLR) ile uygulanan Kullanıcı tanımlı türler (UDTs) için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="23475-104">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="23475-105">CLR SQL Server ile tümleşiktir ve bu mekanizma, veritabanının tür sistemini genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="23475-105">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="23475-106">UDTs, SQL Server veri türü sisteminin kullanıcı genişletilebilirliği ve ayrıca karmaşık yapılandırılmış türleri tanımlama olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="23475-106">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="23475-107">UDTs, bir uygulama mimarisi perspektifinden iki temel avantaj sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="23475-107">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
- <span data-ttu-id="23475-108">İç durum ve dış davranışlar arasında güçlü Kapsülleme (hem istemci hem de sunucu).</span><span class="sxs-lookup"><span data-stu-id="23475-108">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
- <span data-ttu-id="23475-109">Diğer ilgili sunucu özellikleriyle derin tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="23475-109">Deep integration with other related server features.</span></span> <span data-ttu-id="23475-110">Kendi UDT 'nizi tanımladıktan sonra, sütun tanımları ve değişkenler, parametreler, işlev sonuçları, imleçler, Tetikleyiciler ve çoğaltma gibi SQL Server bir sistem türü kullanabileceğiniz tüm bağlamlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23475-110">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="23475-111">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümünün [SQL Server belgelerine](/sql) bakın.</span><span class="sxs-lookup"><span data-stu-id="23475-111">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="23475-112">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="23475-112">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="23475-113">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="23475-113">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="23475-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23475-114">See also</span></span>

- [<span data-ttu-id="23475-115">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="23475-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
