---
title: SQL Üretimi
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 2c18e88967fcba2b8414bfc171412eba908002b3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248410"
---
# <a name="sql-generation"></a><span data-ttu-id="3ea0d-102">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="3ea0d-102">SQL Generation</span></span>
<span data-ttu-id="3ea0d-103">İçin [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]bir sağlayıcı yazdığınızda, komut ağaçlarını, belirli bir veritabanının [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] anlayabileceği şekilde SQL 'e çevirmeniz gerekir, örneğin SQL Server için Transact-SQL veya Oracle için PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="3ea0d-104">Bu bölümde, bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcının SQL oluşturma bileşeni (seçme sorguları için) geliştirmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="3ea0d-105">Ekleme, güncelleştirme ve silme sorguları hakkında daha fazla bilgi için bkz. [DEĞIŞIKLIK SQL oluşturma](modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="3ea0d-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="3ea0d-106">Bu bölümü anlamak için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve ADO.NET sağlayıcı modeliyle ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="3ea0d-107">Komut ağaçlarını ve <xref:System.Data.Common.CommandTrees.DbExpression>de anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="3ea0d-108">SQL oluşturma modülünün rolü</span><span class="sxs-lookup"><span data-stu-id="3ea0d-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="3ea0d-109">Bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcının SQL oluşturma modülü, belirli bir sorgu komut ağacını SQL: 1999 ile uyumlu bir veritabanını hedefleyen tek bir SQL SELECT ifadesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="3ea0d-110">Oluşturulan SQL 'in mümkün olduğunca az sayıda iç içe sorgusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="3ea0d-111">SQL oluşturma modülü çıkış sorgusu komut ağacını basitleştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="3ea0d-112">Bu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , örneğin, birleştirmeleri ortadan kaldırarak ve ardışık filtre düğümlerini daraltarak bu şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="3ea0d-113">Sınıfı, komut <xref:System.Data.Common.DbCommand>ağaçlarını dönüştürmek için SQL oluşturma katmanına erişmenin başlangıç noktasıdır. <xref:System.Data.Common.DbProviderServices></span><span class="sxs-lookup"><span data-stu-id="3ea0d-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ea0d-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3ea0d-114">In This Section</span></span>  
 [<span data-ttu-id="3ea0d-115">Komut Ağaçlarının Şekli</span><span class="sxs-lookup"><span data-stu-id="3ea0d-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="3ea0d-116">Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3ea0d-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="3ea0d-117">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ea0d-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ea0d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ea0d-118">See also</span></span>

- [<span data-ttu-id="3ea0d-119">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="3ea0d-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
