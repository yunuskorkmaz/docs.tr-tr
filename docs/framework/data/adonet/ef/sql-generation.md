---
title: SQL Üretimi
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854359"
---
# <a name="sql-generation"></a><span data-ttu-id="d03b2-102">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="d03b2-102">SQL Generation</span></span>
<span data-ttu-id="d03b2-103">Entity Framework için bir sağlayıcı yazdığınızda, Entity Framework komut ağaçlarını belirli bir veritabanının anlayabilmesi için, SQL Server için Transact-SQL veya Oracle için PL/SQL gibi bir SQL 'e çevirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d03b2-103">When you write a provider for the Entity Framework, you must translate Entity Framework command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="d03b2-104">Bu bölümde, bir Entity Framework sağlayıcısı için SQL oluşturma bileşeni (seçme sorguları için) geliştirmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d03b2-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an Entity Framework provider.</span></span> <span data-ttu-id="d03b2-105">Ekleme, güncelleştirme ve silme sorguları hakkında daha fazla bilgi için bkz. [DEĞIŞIKLIK SQL oluşturma](modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="d03b2-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="d03b2-106">Bu bölümü anlamak için Entity Framework ve ADO.NET sağlayıcı modeliyle ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d03b2-106">To understand this section, you should be familiar with the Entity Framework and the ADO.NET Provider Model.</span></span> <span data-ttu-id="d03b2-107">Komut ağaçlarını ve <xref:System.Data.Common.CommandTrees.DbExpression>de anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d03b2-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="d03b2-108">SQL oluşturma modülünün rolü</span><span class="sxs-lookup"><span data-stu-id="d03b2-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="d03b2-109">Bir Entity Framework sağlayıcının SQL oluşturma modülü, belirli bir sorgu komut ağacını SQL: 1999 ile uyumlu bir veritabanını hedefleyen tek bir SQL SELECT ifadesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d03b2-109">The SQL generation module of an Entity Framework provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="d03b2-110">Oluşturulan SQL 'in mümkün olduğunca az sayıda iç içe sorgusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d03b2-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="d03b2-111">SQL oluşturma modülü çıkış sorgusu komut ağacını basitleştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d03b2-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="d03b2-112">Entity Framework, bu, örneğin birleştirmeleri ortadan kaldırarak ve ardışık filtre düğümlerini daraltarak bu şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="d03b2-112">The Entity Framework will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="d03b2-113">Sınıfı, komut <xref:System.Data.Common.DbCommand>ağaçlarını dönüştürmek için SQL oluşturma katmanına erişmenin başlangıç noktasıdır. <xref:System.Data.Common.DbProviderServices></span><span class="sxs-lookup"><span data-stu-id="d03b2-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d03b2-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d03b2-114">In This Section</span></span>  
 [<span data-ttu-id="d03b2-115">Komut Ağaçlarının Şekli</span><span class="sxs-lookup"><span data-stu-id="d03b2-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="d03b2-116">Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d03b2-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="d03b2-117">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d03b2-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="d03b2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d03b2-118">See also</span></span>

- [<span data-ttu-id="d03b2-119">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="d03b2-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
