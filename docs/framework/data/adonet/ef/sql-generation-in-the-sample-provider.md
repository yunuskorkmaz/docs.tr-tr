---
title: Örnek Sağlayıcısında SQL Oluşturma
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248507"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="30034-102">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="30034-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="30034-103">[Entity Framework örnek sağlayıcı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]tarafından desteklenen ADO.NET veri sağlayıcılarının yeni bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="30034-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="30034-104">SQL Server 2005 veritabanı ile birlikte çalışarak System. Data. SqlClient ADO.NET 2,0 Veri Sağlayıcısı için sarmalayıcı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="30034-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="30034-105">Örnek sağlayıcının SQL oluşturma modülü (örneğin, DmlSqlGenerator.cs dosyası dışında SQL oluşturma klasörü altında bulunur), bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT açıklaması üretir.</span><span class="sxs-lookup"><span data-stu-id="30034-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30034-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="30034-106">In This Section</span></span>  
 <span data-ttu-id="30034-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="30034-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="30034-108">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="30034-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="30034-109">İzlenecek yol: SQL üretimi</span><span class="sxs-lookup"><span data-stu-id="30034-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="30034-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30034-110">See also</span></span>

- [<span data-ttu-id="30034-111">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="30034-111">SQL Generation</span></span>](sql-generation.md)
