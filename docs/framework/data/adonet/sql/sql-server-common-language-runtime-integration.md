---
description: 'Hakkında daha fazla bilgi edinin: SQL Server ortak dil çalışma zamanı tümleştirmesi'
title: SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 096bba0d183526ec8e5d272c5ea6a77ad0778e5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767407"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="f5cc7-103">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="f5cc7-103">SQL Server Common Language Runtime Integration</span></span>

<span data-ttu-id="f5cc7-104">SQL Server 2005, Microsoft Windows için .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirilmesine tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-104">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="f5cc7-105">Bu, Microsoft Visual Basic .NET ve Microsoft Visual C# dahil olmak üzere herhangi bir .NET Framework dilini kullanarak saklı yordamları, Tetikleyicileri, Kullanıcı tanımlı türleri, Kullanıcı tanımlı özellikleri, Kullanıcı tanımlı toplamları ve akış tablosu değerli işlevleri yazabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-105">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="f5cc7-106"><xref:Microsoft.SqlServer.Server>Ad alanı, yönetilen kodun Microsoft SQL Server ortamıyla etkileşime girebilmesi için bir dizi yeni uygulama programlama arabirimi (API) içerir.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-106">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="f5cc7-107">Bu bölümde, SQL Server ortak dil çalışma zamanı (CLR) tümleştirmesine özgü özellikler ve davranışlar ve ADO.NET için işleme özgü SQL Server uzantıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-107">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="f5cc7-108">Bu bölüm, SQL Server CLR tümleştirmesiyle çalışmaya başlamak için yalnızca yeterli bilgi sağlamak amacıyla tasarlanmıştır ve kapsamlı bir şekilde değildir.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-108">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="f5cc7-109">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-109">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="f5cc7-110">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="f5cc7-110">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="f5cc7-111">Ortak dil çalışma zamanı (CLR) tümleştirme programlama kavramları</span><span class="sxs-lookup"><span data-stu-id="f5cc7-111">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a><span data-ttu-id="f5cc7-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f5cc7-112">In This Section</span></span>  

 [<span data-ttu-id="f5cc7-113">SQL Server CLR Tümleştirmesine Giriş</span><span class="sxs-lookup"><span data-stu-id="f5cc7-113">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="f5cc7-114">CLR tümleştirmesi SQL Server için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-114">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="f5cc7-115">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-115">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f5cc7-116">Kullanıcı Tanımlı CLR İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f5cc7-116">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="f5cc7-117">Çeşitli CLR işlevleri türlerinin nasıl uygulanacağını ve kullanılacağını açıklar: tablo değerli, skaler ve Kullanıcı tanımlı toplama işlevleri.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-117">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="f5cc7-118">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="f5cc7-118">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="f5cc7-119">CLR kullanıcı tanımlı türlerin nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-119">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="f5cc7-120">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-120">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f5cc7-121">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="f5cc7-121">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="f5cc7-122">CLR saklı yordamlarının nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-122">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="f5cc7-123">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-123">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f5cc7-124">CLR Tetikleyicileri</span><span class="sxs-lookup"><span data-stu-id="f5cc7-124">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="f5cc7-125">CLR tetikleyicilerinin nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-125">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="f5cc7-126">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-126">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f5cc7-127">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="f5cc7-127">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="f5cc7-128">Bağlam bağlantısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-128">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="f5cc7-129">SQL Server İşlem İçine Özgü ADO.NET Davranışı</span><span class="sxs-lookup"><span data-stu-id="f5cc7-129">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="f5cc7-130">ADO.NET öğesine ve bağlam bağlantısına yönelik işleme özgü uzantıları SQL Server açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-130">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="f5cc7-131">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-131">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cc7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-132">See also</span></span>

- [<span data-ttu-id="f5cc7-133">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5cc7-133">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="f5cc7-134">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5cc7-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
