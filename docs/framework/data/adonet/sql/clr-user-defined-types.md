---
title: Kullanıcı Tanımlı CLR Türleri
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: 84d588e0c415daa7de19ea695c817f3eb24f732f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173594"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="01a92-102">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="01a92-102">CLR User-Defined Types</span></span>

<span data-ttu-id="01a92-103">Microsoft SQL Server, Microsoft .NET Framework ortak dil çalışma zamanı (CLR) ile uygulanan Kullanıcı tanımlı türler (UDTs) için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a92-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="01a92-104">CLR SQL Server ile tümleşiktir ve bu mekanizma, veritabanının tür sistemini genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a92-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="01a92-105">UDTs, SQL Server veri türü sisteminin kullanıcı genişletilebilirliği ve ayrıca karmaşık yapılandırılmış türleri tanımlama olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a92-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="01a92-106">UDTs, bir uygulama mimarisi perspektifinden iki temel avantaj sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="01a92-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
- <span data-ttu-id="01a92-107">İç durum ve dış davranışlar arasında güçlü Kapsülleme (hem istemci hem de sunucu).</span><span class="sxs-lookup"><span data-stu-id="01a92-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
- <span data-ttu-id="01a92-108">Diğer ilgili sunucu özellikleriyle derin tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="01a92-108">Deep integration with other related server features.</span></span> <span data-ttu-id="01a92-109">Kendi UDT 'nizi tanımladıktan sonra, sütun tanımları ve değişkenler, parametreler, işlev sonuçları, imleçler, Tetikleyiciler ve çoğaltma gibi SQL Server bir sistem türü kullanabileceğiniz tüm bağlamlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01a92-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="01a92-110">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümünün [SQL Server belgelerine](/sql) bakın.</span><span class="sxs-lookup"><span data-stu-id="01a92-110">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="01a92-111">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="01a92-111">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="01a92-112">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="01a92-112">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="01a92-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01a92-113">See also</span></span>

- [<span data-ttu-id="01a92-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="01a92-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
