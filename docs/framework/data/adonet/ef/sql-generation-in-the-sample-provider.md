---
title: Örnek sağlayıcısında SQL oluşturma
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: b2397570bb5f312aa6a3955a76234bde508fcc6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505510"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="2d4b2-102">Örnek sağlayıcısında SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d4b2-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="2d4b2-103">[Entity Framework örnek sağlayıcısı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) destekleyen bir ADO.NET veri sağlayıcıları yeni bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d4b2-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="2d4b2-104">SQL Server 2005 veritabanı ile çalışır ve bir sarıcı olarak System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2d4b2-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="2d4b2-105">(' % S'dosyası DmlSqlGenerator.cs dışında SQL oluşturma klasörü altında bulunur) örnek sağlayıcısında SQL oluşturma modülün bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT deyimi üretir.</span><span class="sxs-lookup"><span data-stu-id="2d4b2-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d4b2-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2d4b2-106">In This Section</span></span>  
 <span data-ttu-id="2d4b2-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="2d4b2-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="2d4b2-108">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="2d4b2-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="2d4b2-109">İzlenecek yol: SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d4b2-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d4b2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d4b2-110">See also</span></span>
- [<span data-ttu-id="2d4b2-111">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="2d4b2-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
