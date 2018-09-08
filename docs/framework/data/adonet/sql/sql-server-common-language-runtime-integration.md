---
title: SQL Server ortak dil çalışma zamanı modülü tümleştirmesi
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 5f6c1dcccaddeadb65e6fc949960b0232d00ed81
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137518"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="0c792-102">SQL Server ortak dil çalışma zamanı modülü tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="0c792-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="0c792-103">SQL Server 2005, ortak dil çalışma zamanı (CLR) bileşeni .NET Framework'ün tümleştirme Microsoft Windows için kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="0c792-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="0c792-104">Bu, saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı türler, kullanıcı tarafından tanımlanan İşlevler, kullanıcı tanımlı toplamları ve akış tablo değerli işlevler, Microsoft Visual Basic .NET ve Microsoft da dahil olmak üzere, herhangi bir .NET Framework dili kullanarak yazabildiğinizi anlamına gelir. Visual C#.</span><span class="sxs-lookup"><span data-stu-id="0c792-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="0c792-105"><xref:Microsoft.SqlServer.Server> Ad alanı, yönetilen kod Microsoft SQL Server ortamı ile etkileşimde bulunmasını yeni uygulama programlama arabirimleri (API) kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0c792-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="0c792-106">Bu bölümde, özellikler ve SQL Server ortak dil çalışma zamanı (CLR) tümleştirmesini ve SQL Server işlem içi belirli uzantılar ADO.NET özgü davranışları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c792-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="0c792-107">Bu bölümde, SQL Server CLR Tümleştirmesi ile programlamaya başlamak için yeterli bilgi yalnızca sağlamaya yöneliktir ve kapsamlı olacak şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="0c792-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="0c792-108">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="0c792-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="0c792-109">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="0c792-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="0c792-110">Ortak dil çalışma zamanı (CLR) tümleştirme programlama kavramları</span><span class="sxs-lookup"><span data-stu-id="0c792-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="0c792-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0c792-111">In This Section</span></span>  
 [<span data-ttu-id="0c792-112">SQL Server CLR Tümleştirmesine Giriş</span><span class="sxs-lookup"><span data-stu-id="0c792-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="0c792-113">SQL Server CLR tümleştirmesine giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c792-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="0c792-114">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c792-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0c792-115">Kullanıcı Tanımlı CLR İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0c792-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="0c792-116">Uygulamak ve çeşitli CLR işlevleri kullanmak nasıl açıklar: Tablo değerli, skaler ve kullanıcı tanımlı toplama işlevleri.</span><span class="sxs-lookup"><span data-stu-id="0c792-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="0c792-117">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="0c792-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="0c792-118">Uygulama ve kullanıcı tanımlı CLR türlerini kullanan açıklar.</span><span class="sxs-lookup"><span data-stu-id="0c792-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="0c792-119">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c792-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0c792-120">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="0c792-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="0c792-121">Uygulama ve CLR saklı yordamlar kullanma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="0c792-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="0c792-122">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c792-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0c792-123">CLR Tetikleyicileri</span><span class="sxs-lookup"><span data-stu-id="0c792-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="0c792-124">Uygulama ve CLR Tetikleyicileri kullanma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="0c792-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="0c792-125">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c792-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0c792-126">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="0c792-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="0c792-127">İçerik Bağlantısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0c792-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="0c792-128">SQL Server İşlem İçine Özgü ADO.NET Davranışı</span><span class="sxs-lookup"><span data-stu-id="0c792-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="0c792-129">ADO.NET ve içerik bağlantısı için SQL Server işlem içi belirli uzantılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0c792-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="0c792-130">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c792-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c792-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c792-131">See Also</span></span>  
 [<span data-ttu-id="0c792-132">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0c792-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="0c792-133">Yönetilen kodda SQL Server 2005 nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c792-133">Creating SQL Server 2005 Objects In Managed Code</span></span>](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="0c792-134">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0c792-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
