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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a7f95f7432fdac00a34e7d878ef979656a7af4e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="ac737-102">Örnek Sağlayıcısı'nda SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac737-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="ac737-103">[Entity Framework örnek sağlayıcısı](http://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları yeni bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac737-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="ac737-104">SQL Server 2005 veritabanı ile çalışır ve System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı için bir kapsayıcı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ac737-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="ac737-105">Örnek (dosya DmlSqlGenerator.cs dışında SQL üretme klasörü altında bulunur) sağlayıcı'nın SQL üretimi modülü bir giriş DbQueryCommandTree alır ve tek bir SQL SELECT deyimi üretir.</span><span class="sxs-lookup"><span data-stu-id="ac737-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac737-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac737-106">In This Section</span></span>  
 <span data-ttu-id="ac737-107">Bu bölüm şu konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="ac737-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="ac737-108">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="ac737-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="ac737-109">İzlenecek yol: SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac737-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac737-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac737-110">See Also</span></span>  
 [<span data-ttu-id="ac737-111">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="ac737-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
