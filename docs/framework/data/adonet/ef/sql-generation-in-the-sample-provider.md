---
title: Örnek sağlayıcısında SQL oluşturma
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: cba1cec6d7ef0fdf8d4d4cf6c8e44fb325cf6447
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556211"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="b97ff-102">Örnek sağlayıcısında SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="b97ff-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="b97ff-103">[Entity Framework örnek sağlayıcısı](https://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları yeni bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b97ff-103">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="b97ff-104">SQL Server 2005 veritabanı ile çalışır ve bir sarıcı olarak System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b97ff-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="b97ff-105">(' % S'dosyası DmlSqlGenerator.cs dışında SQL oluşturma klasörü altında bulunur) örnek sağlayıcısında SQL oluşturma modülün bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT deyimi üretir.</span><span class="sxs-lookup"><span data-stu-id="b97ff-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b97ff-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b97ff-106">In This Section</span></span>  
 <span data-ttu-id="b97ff-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="b97ff-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="b97ff-108">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="b97ff-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="b97ff-109">İzlenecek yol: SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b97ff-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="b97ff-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b97ff-110">See Also</span></span>  
 [<span data-ttu-id="b97ff-111">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="b97ff-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
