---
title: SQL Server CLR Tümleştirmesine Giriş
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 41dd89af4f45c673cf6b7283fc39aaf91fd9963c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452415"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="1b2a6-102">SQL Server CLR Tümleştirmesine Giriş</span><span class="sxs-lookup"><span data-stu-id="1b2a6-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="1b2a6-103">Ortak dil çalışma zamanı (CLR) Microsoft .NET çerçevesinin kalbidir ve tüm .NET Framework kodu için yürütme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="1b2a6-104">CLR içinde çalışan kod, yönetilen kod olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="1b2a6-105">CLR, tam zamanında (JıT) derleme, bellek ayırma ve yönetme, tür güvenliğini zorlama, özel durum işleme, iş parçacığı yönetimi ve güvenlik dahil olmak üzere program yürütmesi için gereken çeşitli işlevleri ve hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="1b2a6-106">Microsoft SQL Server içinde barındırılan CLR ile (CLR tümleştirmesi olarak adlandırılır), saklı yordamlar, Tetikleyiciler, Kullanıcı tanımlı işlevler, Kullanıcı tanımlı türler ve Yönetilen koddaki Kullanıcı tanımlı toplamalar yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="1b2a6-107">Yönetilen kod yürütmeden önce yerel koda derlendiğinden, bazı senaryolarda önemli performans artışı elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="1b2a6-108">Yönetilen kod, derlemelerin belirli işlemleri gerçekleştirmesini engellemek için kod erişim güvenliği (CAS), kod bağlantıları ve uygulama etki alanları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="1b2a6-109">SQL Server, yönetilen kodun güvenliğini sağlamak ve işletim sisteminin veya veritabanı sunucusunun güvenliğinin aşılmasına engel olmak için CAS kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="1b2a6-110">Bu bölüm, SQL Server CLR tümleştirmesiyle çalışmaya başlamak için yalnızca yeterli bilgi sağlamak amacıyla tasarlanmıştır ve kapsamlı bir şekilde değildir.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="1b2a6-111">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="1b2a6-112">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="1b2a6-112">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="1b2a6-113">Ortak dil çalışma zamanı (CLR) tümleştirmesine genel bakış</span><span class="sxs-lookup"><span data-stu-id="1b2a6-113">Common Language Runtime (CLR) Integration Overview</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-integration-overview)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="1b2a6-114">CLR tümleştirmesini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1b2a6-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="1b2a6-115">Ortak dil çalışma zamanı (CLR) tümleştirme özelliği Microsoft SQL Server ' de varsayılan olarak kapalıdır ve CLR tümleştirmesi kullanılarak uygulanan nesneleri kullanabilmek için etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="1b2a6-116">Transact-SQL kullanarak CLR tümleştirmesini etkinleştirmek için, `sp_configure` saklı yordamının `clr enabled` seçeneğini gösterildiği gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="1b2a6-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="1b2a6-117">`clr enabled` seçeneğini 0 olarak ayarlayarak CLR tümleştirmesini devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="1b2a6-118">CLR tümleştirmesini devre dışı bıraktığınızda, SQL Server tüm CLR yordamlarını yürütmeyi durduruyor ve tüm uygulama etki alanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="1b2a6-119">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="1b2a6-120">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="1b2a6-120">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="1b2a6-121">CLR tümleştirmesini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1b2a6-121">Enabling CLR Integration</span></span>](/sql/relational-databases/clr-integration/clr-integration-enabling)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="1b2a6-122">CLR derlemesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="1b2a6-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="1b2a6-123">CLR yöntemleri test sunucusunda sınandıktan ve doğrulandıktan sonra, bir dağıtım betiği kullanılarak üretim sunucularına dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="1b2a6-124">Dağıtım betiği el ile veya SQL Server Management Studio kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="1b2a6-125">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-125">For more detailed information, see the version of SQL Server documentation for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="1b2a6-126">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="1b2a6-126">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="1b2a6-127">CLR veritabanı nesnelerini dağıtma</span><span class="sxs-lookup"><span data-stu-id="1b2a6-127">Deploying CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/deploying-clr-database-objects)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="1b2a6-128">CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="1b2a6-128">CLR Integration Security</span></span>  
 <span data-ttu-id="1b2a6-129">Microsoft .NET Framework ortak dil çalışma zamanı (CLR) ile Microsoft SQL Server tümleştirme güvenlik modeli, SQL Server içinde çalışan farklı CLR türleri ve CLR olmayan nesneler arasındaki erişimi yönetir ve güvenliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="1b2a6-130">Bu nesneler bir Transact-SQL ifadesiyle veya sunucuda çalışan başka bir CLR nesnesi tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="1b2a6-131">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="1b2a6-132">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="1b2a6-132">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="1b2a6-133">CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="1b2a6-133">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="1b2a6-134">CLR derlemesinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b2a6-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="1b2a6-135">Microsoft SQL Server, veritabanında Transact-SQL ve ortak dil çalışma zamanı (CLR) nesnelerinde hata ayıklama desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="1b2a6-136">Diller arasında çalışma hatalarını ayıklama: kullanıcılar Transact-SQL ' t e n CLR nesneleri ile sorunsuz bir şekilde çalışabilir ve bunun tersini yapabilir.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="1b2a6-137">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="1b2a6-138">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="1b2a6-138">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="1b2a6-139">CLR veritabanı nesnelerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b2a6-139">Debugging CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/debugging-clr-database-objects)  
  
## <a name="see-also"></a><span data-ttu-id="1b2a6-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b2a6-140">See also</span></span>

- [<span data-ttu-id="1b2a6-141">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1b2a6-141">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="1b2a6-142">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1b2a6-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
