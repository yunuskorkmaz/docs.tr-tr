---
title: Örnek sağlayıcısında SQL oluşturma
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 5aa6e31cfc93a4ae1871da63f466864b4ea6f5d9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149724"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="18839-102">Örnek sağlayıcısında SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="18839-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="18839-103">[Entity Framework örnek sağlayıcısı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) destekleyen bir ADO.NET veri sağlayıcıları yeni bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18839-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="18839-104">SQL Server 2005 veritabanı ile çalışır ve bir sarıcı olarak System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="18839-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="18839-105">(' % S'dosyası DmlSqlGenerator.cs dışında SQL oluşturma klasörü altında bulunur) örnek sağlayıcısında SQL oluşturma modülün bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT deyimi üretir.</span><span class="sxs-lookup"><span data-stu-id="18839-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18839-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="18839-106">In This Section</span></span>  
 <span data-ttu-id="18839-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="18839-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="18839-108">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="18839-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="18839-109">İzlenecek yol: SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="18839-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="18839-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18839-110">See Also</span></span>  
 [<span data-ttu-id="18839-111">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="18839-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
