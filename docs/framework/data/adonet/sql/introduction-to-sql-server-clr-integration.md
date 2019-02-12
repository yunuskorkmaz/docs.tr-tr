---
title: SQL Server CLR tümleştirmesine giriş
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dcfc43a68fb8bcacd4a14d6b94a932d656635d55
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092585"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="9e069-102">SQL Server CLR tümleştirmesine giriş</span><span class="sxs-lookup"><span data-stu-id="9e069-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="9e069-103">Ortak dil çalışma zamanı (CLR), Microsoft .NET Framework kalbidir ve tüm .NET Framework kod yürütme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e069-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="9e069-104">CLR içinde çalışan kod, yönetilen kod olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9e069-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="9e069-105">CLR, ayırma ve bellek, tür güvenliği, özel durum işleme, iş parçacığı yönetimi ve güvenlik zorlama yönetme çeşitli işlevleri ve tam zamanında (JIT) derleme dahil olmak üzere, program yürütme için gerekli hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e069-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="9e069-106">Microsoft SQL Server (CLR tümleştirme olarak adlandırılır) barındırılan CLR ile saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı işlevleri, kullanıcı tanımlı türler ve kullanıcı tanımlı toplamlarda yönetilen kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e069-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="9e069-107">Yürütme önce yerel kod için yönetilen kodu derler olduğundan, bazı senaryolarda önemli performans artışları elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e069-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="9e069-108">Yönetilen kod kullandığı kod erişim güvenliği (CAS), kodu bağlantıları ve belirli işlemleri gerçekleştirmeyi derlemeleri önlemek için uygulama etki alanları.</span><span class="sxs-lookup"><span data-stu-id="9e069-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="9e069-109">Yönetilen kod güvenli ve veritabanı sunucusu ve işletim sistemi güvenliğinin aşılması önlemeye yardımcı olmak için CAS SQL Server kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e069-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="9e069-110">Bu bölümde, SQL Server CLR Tümleştirmesi ile programlamaya başlamak için yeterli bilgi yalnızca sağlamaya yöneliktir ve kapsamlı olacak şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="9e069-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="9e069-111">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="9e069-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9e069-112">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="9e069-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="9e069-113">Ortak dil çalışma zamanı (CLR) tümleştirme genel bakış</span><span class="sxs-lookup"><span data-stu-id="9e069-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="9e069-114">CLR tümleştirmesini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9e069-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="9e069-115">Ortak dil çalışma zamanı (CLR) tümleştirme özelliği, Microsoft SQL Server'da varsayılan olarak kapalıdır ve CLR tümleştirmesini kullanılarak yüklenen nesneler kullanmak için etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e069-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="9e069-116">Transact-SQL kullanarak CLR tümleştirmesini etkinleştirmek için `clr enabled` seçeneği `sp_configure` gösterildiği saklı yordam:</span><span class="sxs-lookup"><span data-stu-id="9e069-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="9e069-117">Ayarlayarak CLR tümleştirmesini devre dışı bırakabilirsiniz `clr enabled` seçeneğini 0.</span><span class="sxs-lookup"><span data-stu-id="9e069-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="9e069-118">CLR tümleştirmesini devre dışı bıraktığınızda, SQL Server CLR tüm yordamları yürütme durdurur ve tüm uygulama etki alanları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9e069-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="9e069-119">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="9e069-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9e069-120">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="9e069-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="9e069-121">CLR tümleştirmesini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9e069-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="9e069-122">Bir CLR derlemesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="9e069-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="9e069-123">CLR yöntemleri test ve test sunucusunda doğrulandı sonra dağıtım betiğini kullanarak üretim sunucularına dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e069-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="9e069-124">Dağıtım betiği, el ile veya SQL Server Management Studio kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="9e069-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="9e069-125">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="9e069-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9e069-126">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="9e069-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="9e069-127">CLR veritabanı nesneleri dağıtma</span><span class="sxs-lookup"><span data-stu-id="9e069-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="9e069-128">CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="9e069-128">CLR Integration Security</span></span>  
 <span data-ttu-id="9e069-129">Microsoft .NET Framework ortak dil çalışma zamanı (CLR) ile Microsoft SQL Server Tümleştirme güvenlik modelinin yönetir ve farklı içinde SQL Server çalıştıran CLR ve CLR olmayan nesneler arasında erişim güvenliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e069-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="9e069-130">Bu nesneler, bir Transact-SQL deyimi veya server çalıştıran başka bir CLR nesnesi tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e069-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="9e069-131">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="9e069-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9e069-132">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="9e069-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="9e069-133">CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="9e069-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="9e069-134">Bir CLR derlemesi hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9e069-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="9e069-135">Microsoft SQL Server Transact-SQL ve ortak dil çalışma zamanı (CLR) nesneleri veritabanındaki hata ayıklama için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e069-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="9e069-136">Diller arasında çalışan hata ayıklama: kullanıcılar adım sorunsuz bir şekilde CLR nesnelerini Transact-SQL'den ve bunun tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9e069-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="9e069-137">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="9e069-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9e069-138">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="9e069-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="9e069-139">Hata ayıklama CLR veritabanı nesneleri</span><span class="sxs-lookup"><span data-stu-id="9e069-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="9e069-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e069-140">See also</span></span>
- [<span data-ttu-id="9e069-141">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e069-141">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="9e069-142">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9e069-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
