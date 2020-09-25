---
title: SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d9fe0f03c88584607c6bc38fcbcff3f9424fd40c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183032"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="dd6cb-102">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="dd6cb-102">SQL Server Common Language Runtime Integration</span></span>

<span data-ttu-id="dd6cb-103">SQL Server 2005, Microsoft Windows için .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirilmesine tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="dd6cb-104">Bu, Microsoft Visual Basic .NET ve Microsoft Visual C# dahil olmak üzere herhangi bir .NET Framework dilini kullanarak saklı yordamları, Tetikleyicileri, Kullanıcı tanımlı türleri, Kullanıcı tanımlı özellikleri, Kullanıcı tanımlı toplamları ve akış tablosu değerli işlevleri yazabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="dd6cb-105"><xref:Microsoft.SqlServer.Server>Ad alanı, yönetilen kodun Microsoft SQL Server ortamıyla etkileşime girebilmesi için bir dizi yeni uygulama programlama arabirimi (API) içerir.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="dd6cb-106">Bu bölümde, SQL Server ortak dil çalışma zamanı (CLR) tümleştirmesine özgü özellikler ve davranışlar ve ADO.NET için işleme özgü SQL Server uzantıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="dd6cb-107">Bu bölüm, SQL Server CLR tümleştirmesiyle çalışmaya başlamak için yalnızca yeterli bilgi sağlamak amacıyla tasarlanmıştır ve kapsamlı bir şekilde değildir.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="dd6cb-108">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="dd6cb-109">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="dd6cb-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="dd6cb-110">Ortak dil çalışma zamanı (CLR) tümleştirme programlama kavramları</span><span class="sxs-lookup"><span data-stu-id="dd6cb-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a><span data-ttu-id="dd6cb-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dd6cb-111">In This Section</span></span>  

 [<span data-ttu-id="dd6cb-112">SQL Server CLR Tümleştirmesine Giriş</span><span class="sxs-lookup"><span data-stu-id="dd6cb-112">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="dd6cb-113">CLR tümleştirmesi SQL Server için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="dd6cb-114">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="dd6cb-115">Kullanıcı Tanımlı CLR İşlevleri</span><span class="sxs-lookup"><span data-stu-id="dd6cb-115">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="dd6cb-116">Çeşitli CLR işlevleri türlerinin nasıl uygulanacağını ve kullanılacağını açıklar: tablo değerli, skaler ve Kullanıcı tanımlı toplama işlevleri.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="dd6cb-117">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="dd6cb-117">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="dd6cb-118">CLR kullanıcı tanımlı türlerin nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="dd6cb-119">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="dd6cb-120">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="dd6cb-120">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="dd6cb-121">CLR saklı yordamlarının nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="dd6cb-122">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="dd6cb-123">CLR Tetikleyicileri</span><span class="sxs-lookup"><span data-stu-id="dd6cb-123">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="dd6cb-124">CLR tetikleyicilerinin nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="dd6cb-125">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="dd6cb-126">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="dd6cb-126">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="dd6cb-127">Bağlam bağlantısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="dd6cb-128">SQL Server İşlem İçine Özgü ADO.NET Davranışı</span><span class="sxs-lookup"><span data-stu-id="dd6cb-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="dd6cb-129">ADO.NET öğesine ve bağlam bağlantısına yönelik işleme özgü uzantıları SQL Server açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="dd6cb-130">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd6cb-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd6cb-131">See also</span></span>

- [<span data-ttu-id="dd6cb-132">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd6cb-132">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="dd6cb-133">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd6cb-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
