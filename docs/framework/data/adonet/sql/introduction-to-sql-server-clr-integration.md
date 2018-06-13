---
title: SQL Server CLR tümleştirmesine giriş
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dd0ef041db13aa842554c70533770bf99c369941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365585"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="10035-102">SQL Server CLR tümleştirmesine giriş</span><span class="sxs-lookup"><span data-stu-id="10035-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="10035-103">Ortak dil çalışma zamanı (CLR) Microsoft .NET Framework'ün Kalp ve tüm .NET Framework kod yürütme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="10035-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="10035-104">CLR çalışan kod yönetilen kodu olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="10035-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="10035-105">CLR ayırma ve tür güvenliği, özel durum işleme, iş parçacığı yönetimi ve güvenlik zorlamayı bellek yönetme çeşitli işlevleri ve tam zamanında (JIT) derleme dahil olmak üzere, program yürütme için gerekli hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="10035-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="10035-106">Microsoft SQL Server (CLR tümleştirmesini denir) barındırılan CLR ile saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı işlevler, kullanıcı tanımlı türler ve kullanıcı tanımlı toplamlarda yönetilen kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10035-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="10035-107">Yönetilen kod yürütme önce yerel koda derlenen çünkü bazı senaryolarda önemli ölçüde performans artışı elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10035-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="10035-108">Yönetilen kod erişim güvenliği (CAS) kodu kullanır, kod bağlantılar ve belirli işlemleri gerçekleştirmeyi derlemeleri önlemek için uygulama etki alanları.</span><span class="sxs-lookup"><span data-stu-id="10035-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="10035-109">SQL Server CA'lar yönetilen kod güvenli ve veritabanı sunucusu ve işletim sistemi güvenliğinin aşılması önlemeye yardımcı olmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="10035-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="10035-110">Bu bölümde, SQL Server CLR Tümleştirmesi ile programlamaya başlamak için yeterli bilgi yalnızca sağlamak için tasarlanmıştır ve kapsamlı olması düşünülmemiştir.</span><span class="sxs-lookup"><span data-stu-id="10035-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="10035-111">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="10035-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="10035-112">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="10035-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="10035-113">Ortak dil çalışma zamanı (CLR) tümleştirme genel bakış</span><span class="sxs-lookup"><span data-stu-id="10035-113">Common Language Runtime (CLR) Integration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="10035-114">CLR tümleştirmesini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="10035-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="10035-115">Ortak dil çalışma zamanı (CLR) tümleştirme özelliği, Microsoft SQL Server'da varsayılan olarak kapalıdır ve CLR tümleştirmesini kullanılarak uygulanan nesneleri kullanmak için etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="10035-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="10035-116">Transact-SQL kullanarak CLR tümleştirmesini etkinleştirmek için `clr enabled` seçeneği `sp_configure` saklı yordamı gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="10035-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="10035-117">Ayarlayarak CLR tümleştirmesini devre dışı bırakabilirsiniz `clr enabled` 0 seçeneği.</span><span class="sxs-lookup"><span data-stu-id="10035-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="10035-118">CLR tümleştirmesini devre dışı bıraktığınızda, SQL Server tüm CLR yordamları çalıştırma durdurur ve tüm uygulama etki alanları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="10035-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="10035-119">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="10035-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="10035-120">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="10035-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="10035-121">CLR tümleştirmesini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="10035-121">Enabling CLR Integration</span></span>](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="10035-122">CLR derlemesinde dağıtma</span><span class="sxs-lookup"><span data-stu-id="10035-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="10035-123">CLR yöntemleri test ve test sunucusunda doğruladıktan sonra bir dağıtım komut dosyası kullanarak üretim sunucularına dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="10035-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="10035-124">Dağıtım betiği el ile veya SQL Server Management Studio'yu kullanarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="10035-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="10035-125">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="10035-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="10035-126">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="10035-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="10035-127">CLR veritabanı nesnelerini dağıtma</span><span class="sxs-lookup"><span data-stu-id="10035-127">Deploying CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="10035-128">CLR tümleştirme güvenlik</span><span class="sxs-lookup"><span data-stu-id="10035-128">CLR Integration Security</span></span>  
 <span data-ttu-id="10035-129">Microsoft .NET Framework ortak dil çalışma zamanı (CLR) ile Microsoft SQL Server Tümleştirme güvenlik modelinin yönetir ve SQL Server'ın içinde çalışan CLR ve CLR olmayan nesneler farklı türleri arasında erişim güvenliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="10035-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="10035-130">Bu nesneler, bir Transact-SQL deyimi veya sunucusunda çalışan başka bir CLR nesnesi tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="10035-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="10035-131">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="10035-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="10035-132">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="10035-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="10035-133">CLR tümleştirme güvenlik</span><span class="sxs-lookup"><span data-stu-id="10035-133">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="10035-134">CLR derlemesinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="10035-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="10035-135">Microsoft SQL Server Transact-SQL ve ortak dil çalışma zamanı (CLR) nesneleri veritabanındaki hata ayıklama için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="10035-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="10035-136">Works dillerde hata ayıklama: kullanıcılar adım sorunsuz bir şekilde CLR nesnelerini Transact-SQL, bunun tam tersi.</span><span class="sxs-lookup"><span data-stu-id="10035-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="10035-137">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="10035-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="10035-138">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="10035-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="10035-139">CLR veritabanı nesnelerini hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="10035-139">Debugging CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="10035-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10035-140">See Also</span></span>  
 [<span data-ttu-id="10035-141">Yönetilen kodda SQL Server 2005'te nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="10035-141">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="10035-142">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="10035-142">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="10035-143">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="10035-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
