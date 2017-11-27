---
title: "Örnek Sağlayıcısı'nda SQL oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58a49f7bf5d385466810a3c59bda748ef66d5840
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="d2ab4-102">Örnek Sağlayıcısı'nda SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2ab4-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="d2ab4-103">[Entity Framework örnek sağlayıcısı](http://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları yeni bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2ab4-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="d2ab4-104">SQL Server 2005 veritabanı ile çalışır ve System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı için bir kapsayıcı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d2ab4-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="d2ab4-105">Örnek (dosya DmlSqlGenerator.cs dışında SQL üretme klasörü altında bulunur) sağlayıcı'nın SQL üretimi modülü bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT deyimi üretir.</span><span class="sxs-lookup"><span data-stu-id="d2ab4-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d2ab4-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d2ab4-106">In This Section</span></span>  
 <span data-ttu-id="d2ab4-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="d2ab4-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="d2ab4-108">Mimari ve tasarım</span><span class="sxs-lookup"><span data-stu-id="d2ab4-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="d2ab4-109">İzlenecek yol: SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2ab4-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2ab4-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2ab4-110">See Also</span></span>  
 [<span data-ttu-id="d2ab4-111">SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2ab4-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
