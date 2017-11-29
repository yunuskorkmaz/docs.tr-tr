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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 727aa0ca3e1673a5bbd29884077ed5aa65d792f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation"></a><span data-ttu-id="5fb49-102">SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fb49-102">SQL Generation</span></span>
<span data-ttu-id="5fb49-103">Sağlayıcı için yazdığınız zaman [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], çevir gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belirli bir veritabanı için SQL Server Transact-SQL veya PL/SQL Oracle için gibi anlayabileceği SQL içine ağaçları komutu.</span><span class="sxs-lookup"><span data-stu-id="5fb49-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="5fb49-104">Bu bölümde, için bir SQL oluşturma bileşeni (için SELECT sorgular) geliştirme hakkında bilgi edineceksiniz bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5fb49-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="5fb49-105">Ekleme hakkında bilgi, güncelleştirme ve sorguları silmek için bkz: [değişikliği SQL üretimi](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="5fb49-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="5fb49-106">Bu bölümde anlamak için aşina olmalısınız [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve ADO.NET sağlayıcısı modeli.</span><span class="sxs-lookup"><span data-stu-id="5fb49-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="5fb49-107">Komut ağaçlarını anlamanız gerekir ve <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="5fb49-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="5fb49-108">SQL oluşturma modülü rolü</span><span class="sxs-lookup"><span data-stu-id="5fb49-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="5fb49-109">SQL nesil modül, bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcı çevirir verilen sorgu komut ağacındaki bir SQL:1999 hedefleyen bir tek SQL SELECT INTO deyimi-uyumlu veritabanı.</span><span class="sxs-lookup"><span data-stu-id="5fb49-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="5fb49-110">Oluşturulan SQL az sayıda sorguları mümkün olduğunca iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="5fb49-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="5fb49-111">SQL oluşturma modülü çıkış sorgu komut ağacı basitleştirmek değil.</span><span class="sxs-lookup"><span data-stu-id="5fb49-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="5fb49-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bu, örneğin birleştirmeler kaldırarak ve ardışık filtre düğümlerinin daraltma işlemi yapar.</span><span class="sxs-lookup"><span data-stu-id="5fb49-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="5fb49-113"><!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices` Sınıfı komutu ağaçlara dönüştürmek için SQL nesil katman erişmek için başlangıç noktasıdır <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.</span><span class="sxs-lookup"><span data-stu-id="5fb49-113">The <!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices`  class is the starting point for accessing the SQL generation layer to convert command trees into <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5fb49-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5fb49-114">In This Section</span></span>  
 [<span data-ttu-id="5fb49-115">Komut ağaçlarını şekli</span><span class="sxs-lookup"><span data-stu-id="5fb49-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="5fb49-116">SQL komut ağaçlarını - en iyi uygulamaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fb49-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="5fb49-117">Örnek Sağlayıcısı'nda SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fb49-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="5fb49-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fb49-118">See Also</span></span>  
 [<span data-ttu-id="5fb49-119">Bir Entity Framework veri sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="5fb49-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
