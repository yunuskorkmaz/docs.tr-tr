---
title: Örnek Sağlayıcısı'nda SQL oluşturma
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 7275a67927d7692dc943e2555d65d1f7d6e4ba5a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762159"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="3bb86-102">Örnek Sağlayıcısı'nda SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bb86-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="3bb86-103">[Entity Framework örnek sağlayıcısı](http://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları yeni bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3bb86-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="3bb86-104">SQL Server 2005 veritabanı ile çalışır ve System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı için bir kapsayıcı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3bb86-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="3bb86-105">Örnek (dosya DmlSqlGenerator.cs dışında SQL üretme klasörü altında bulunur) sağlayıcı'nın SQL üretimi modülü bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT deyimi üretir.</span><span class="sxs-lookup"><span data-stu-id="3bb86-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bb86-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3bb86-106">In This Section</span></span>  
 <span data-ttu-id="3bb86-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="3bb86-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="3bb86-108">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="3bb86-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="3bb86-109">İzlenecek yol: SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bb86-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="3bb86-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3bb86-110">See Also</span></span>  
 [<span data-ttu-id="3bb86-111">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="3bb86-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
