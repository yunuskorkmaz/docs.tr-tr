---
title: "SQL oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6b2d4ba925af61f89b47c494f5fb17f5f9f0d995
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation"></a><span data-ttu-id="36f50-102">SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="36f50-102">SQL Generation</span></span>
<span data-ttu-id="36f50-103">Sağlayıcı için yazdığınız zaman [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], çevir gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belirli bir veritabanı için SQL Server Transact-SQL veya PL/SQL Oracle için gibi anlayabileceği SQL içine ağaçları komutu.</span><span class="sxs-lookup"><span data-stu-id="36f50-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="36f50-104">Bu bölümde, için bir SQL oluşturma bileşeni (için SELECT sorgular) geliştirme hakkında bilgi edineceksiniz bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="36f50-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="36f50-105">Ekleme hakkında bilgi, güncelleştirme ve sorguları silmek için bkz: [değişikliği SQL üretimi](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="36f50-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="36f50-106">Bu bölümde anlamak için aşina olmalısınız [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve ADO.NET sağlayıcısı modeli.</span><span class="sxs-lookup"><span data-stu-id="36f50-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="36f50-107">Komut ağaçlarını anlamanız gerekir ve <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="36f50-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="36f50-108">SQL oluşturma modülü rolü</span><span class="sxs-lookup"><span data-stu-id="36f50-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="36f50-109">SQL nesil modül, bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcı çevirir verilen sorgu komut ağacındaki bir SQL:1999 hedefleyen bir tek SQL SELECT INTO deyimi-uyumlu veritabanı.</span><span class="sxs-lookup"><span data-stu-id="36f50-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="36f50-110">Oluşturulan SQL az sayıda sorguları mümkün olduğunca iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="36f50-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="36f50-111">SQL oluşturma modülü çıkış sorgu komut ağacı basitleştirmek değil.</span><span class="sxs-lookup"><span data-stu-id="36f50-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="36f50-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bu, örneğin birleştirmeler kaldırarak ve ardışık filtre düğümlerinin daraltma işlemi yapar.</span><span class="sxs-lookup"><span data-stu-id="36f50-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="36f50-113"><xref:System.Data.Common.DbProviderServices> Sınıfı komutu ağaçlara dönüştürmek için SQL nesil katman erişmek için başlangıç noktasıdır <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="36f50-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36f50-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="36f50-114">In This Section</span></span>  
 [<span data-ttu-id="36f50-115">Komut Ağaçlarının Şekli</span><span class="sxs-lookup"><span data-stu-id="36f50-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="36f50-116">Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="36f50-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="36f50-117">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="36f50-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="36f50-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36f50-118">See Also</span></span>  
 [<span data-ttu-id="36f50-119">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="36f50-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
