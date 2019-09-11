---
title: Örnek Sağlayıcısında SQL Oluşturma
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854324"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="5fb79-102">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fb79-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="5fb79-103">[Entity Framework örnek sağlayıcı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , Entity Framework destekleyen yeni ADO.NET veri sağlayıcılarının bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fb79-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the Entity Framework.</span></span>  <span data-ttu-id="5fb79-104">SQL Server 2005 veritabanı ile birlikte çalışarak System. Data. SqlClient ADO.NET 2,0 Veri Sağlayıcısı için sarmalayıcı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5fb79-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="5fb79-105">Örnek sağlayıcının SQL oluşturma modülü (örneğin, DmlSqlGenerator.cs dosyası dışında SQL oluşturma klasörü altında bulunur), bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT açıklaması üretir.</span><span class="sxs-lookup"><span data-stu-id="5fb79-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5fb79-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5fb79-106">In This Section</span></span>  
 <span data-ttu-id="5fb79-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="5fb79-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="5fb79-108">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="5fb79-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="5fb79-109">İzlenecek yol: SQL üretimi</span><span class="sxs-lookup"><span data-stu-id="5fb79-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="5fb79-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fb79-110">See also</span></span>

- [<span data-ttu-id="5fb79-111">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="5fb79-111">SQL Generation</span></span>](sql-generation.md)
