---
title: "SQL Server ortak dil çalışma zamanı tümleştirmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bccf3a50aabe991f09217f501d14b6f9337d76ba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="5959c-102">SQL Server ortak dil çalışma zamanı tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="5959c-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="5959c-103">.NET Framework ortak dil çalışma zamanı (CLR) bileşeni tümleştirme Windows için Microsoft SQL Server 2005 sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="5959c-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="5959c-104">Bu, saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı türler, kullanıcı tanımlı işlevler, kullanıcı tanımlı toplamlarda ve akış tablo değerli işlevler, Microsoft Visual Basic .NET ve Microsoft dahil olmak üzere, herhangi bir .NET Framework dil kullanarak yazabildiğinizi anlamına gelir. Visual C#.</span><span class="sxs-lookup"><span data-stu-id="5959c-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="5959c-105"><xref:Microsoft.SqlServer.Server> Ad alanı, böylece yönetilen kod ile Microsoft SQL Server ortamını etkileşim kurabilen bir dizi yeni uygulama programlama arabirimleri (API) içerir.</span><span class="sxs-lookup"><span data-stu-id="5959c-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="5959c-106">Bu bölümde, özellikleri ve SQL Server ortak dil çalışma zamanı (CLR) tümleştirmesini ve SQL Server işlem içi belirli uzantılar ADO.NET özgü davranışları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5959c-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="5959c-107">Bu bölümde, SQL Server CLR Tümleştirmesi ile programlamaya başlamak için yeterli bilgi yalnızca sağlamak için tasarlanmıştır ve kapsamlı olması düşünülmemiştir.</span><span class="sxs-lookup"><span data-stu-id="5959c-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="5959c-108">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="5959c-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="5959c-109">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="5959c-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="5959c-110">Ortak dil çalışma zamanı (CLR) tümleştirmesini programlama kavramları</span><span class="sxs-lookup"><span data-stu-id="5959c-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](http://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="5959c-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5959c-111">In This Section</span></span>  
 [<span data-ttu-id="5959c-112">SQL Server CLR Tümleştirmesine Giriş</span><span class="sxs-lookup"><span data-stu-id="5959c-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="5959c-113">SQL Server CLR tümleştirmesi tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5959c-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="5959c-114">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5959c-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5959c-115">Kullanıcı Tanımlı CLR İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5959c-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="5959c-116">CLR işlevleri çeşitli türleri uygulamak ve nasıl kullanılacağını açıklar: Tablo değerli, skaler ve kullanıcı tanımlı toplama işlevleri.</span><span class="sxs-lookup"><span data-stu-id="5959c-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="5959c-117">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="5959c-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="5959c-118">CLR kullanıcı tanımlı türler uygulamak ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5959c-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="5959c-119">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5959c-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5959c-120">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="5959c-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="5959c-121">CLR saklı yordamları uygulayın ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5959c-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="5959c-122">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5959c-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5959c-123">CLR Tetikleyicileri</span><span class="sxs-lookup"><span data-stu-id="5959c-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="5959c-124">CLR Tetikleyiciler uygulamak ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5959c-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="5959c-125">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5959c-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5959c-126">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="5959c-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="5959c-127">İçerik Bağlantısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5959c-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="5959c-128">SQL Server İşlem İçine Özgü ADO.NET Davranışı</span><span class="sxs-lookup"><span data-stu-id="5959c-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="5959c-129">SQL Server işlem içi belirli uzantılara ADO.NET ve içerik bağlantısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5959c-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="5959c-130">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5959c-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5959c-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5959c-131">See Also</span></span>  
 [<span data-ttu-id="5959c-132">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5959c-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="5959c-133">Yönetilen kodda SQL Server 2005'te nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5959c-133">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="5959c-134">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="5959c-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
