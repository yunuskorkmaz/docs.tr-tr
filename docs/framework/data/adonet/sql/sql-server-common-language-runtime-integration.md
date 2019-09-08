---
title: SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 77b40c6a1576b87d9bb4a7eb4b1ee3df8828b892
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780863"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="2757d-102">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="2757d-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="2757d-103">SQL Server 2005, Microsoft Windows için .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirilmesine tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2757d-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="2757d-104">Bu, Microsoft Visual Basic .NET ve Microsoft dahil olmak üzere herhangi bir .NET Framework dilini kullanarak saklı yordamları, Tetikleyicileri, Kullanıcı tanımlı türleri, Kullanıcı tanımlı özellikleri, Kullanıcı tanımlı toplamları ve akış tablosu değerli işlevleri yazabileceğiniz anlamına gelir. Görsel C#.</span><span class="sxs-lookup"><span data-stu-id="2757d-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="2757d-105">Ad <xref:Microsoft.SqlServer.Server> alanı, yönetilen kodun Microsoft SQL Server ortamıyla etkileşime girebilmesi için bir dizi yeni uygulama programlama arabirimi (API) içerir.</span><span class="sxs-lookup"><span data-stu-id="2757d-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="2757d-106">Bu bölümde, SQL Server ortak dil çalışma zamanı (CLR) tümleştirmesine özgü özellikler ve davranışlar ve ADO.NET için işleme özgü SQL Server uzantıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2757d-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="2757d-107">Bu bölüm, SQL Server CLR tümleştirmesiyle çalışmaya başlamak için yalnızca yeterli bilgi sağlamak amacıyla tasarlanmıştır ve kapsamlı bir şekilde değildir.</span><span class="sxs-lookup"><span data-stu-id="2757d-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="2757d-108">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2757d-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="2757d-109">**Books Online SQL Server**</span><span class="sxs-lookup"><span data-stu-id="2757d-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="2757d-110">Ortak dil çalışma zamanı (CLR) tümleştirme programlama kavramları</span><span class="sxs-lookup"><span data-stu-id="2757d-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="2757d-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2757d-111">In This Section</span></span>  
 [<span data-ttu-id="2757d-112">SQL Server CLR Tümleştirmesine Giriş</span><span class="sxs-lookup"><span data-stu-id="2757d-112">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="2757d-113">CLR tümleştirmesi SQL Server için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="2757d-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="2757d-114">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2757d-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="2757d-115">Kullanıcı Tanımlı CLR İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2757d-115">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="2757d-116">Çeşitli CLR işlevleri türlerinin nasıl uygulanacağını ve kullanılacağını açıklar: tablo değerli, skaler ve Kullanıcı tanımlı toplama işlevleri.</span><span class="sxs-lookup"><span data-stu-id="2757d-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="2757d-117">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="2757d-117">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="2757d-118">CLR kullanıcı tanımlı türlerin nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2757d-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="2757d-119">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2757d-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="2757d-120">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="2757d-120">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="2757d-121">CLR saklı yordamlarının nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2757d-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="2757d-122">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2757d-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="2757d-123">CLR Tetikleyicileri</span><span class="sxs-lookup"><span data-stu-id="2757d-123">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="2757d-124">CLR tetikleyicilerinin nasıl uygulanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2757d-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="2757d-125">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2757d-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="2757d-126">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="2757d-126">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="2757d-127">Bağlam bağlantısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2757d-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="2757d-128">SQL Server İşlem İçine Özgü ADO.NET Davranışı</span><span class="sxs-lookup"><span data-stu-id="2757d-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="2757d-129">ADO.NET öğesine ve bağlam bağlantısına yönelik işleme özgü uzantıları SQL Server açıklar.</span><span class="sxs-lookup"><span data-stu-id="2757d-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="2757d-130">Ek konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2757d-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2757d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2757d-131">See also</span></span>

- [<span data-ttu-id="2757d-132">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2757d-132">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="2757d-133">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2757d-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
