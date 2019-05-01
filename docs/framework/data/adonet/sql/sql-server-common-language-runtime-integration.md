---
title: SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: fd043aa6c7e5b9246a36146e000e5cba9e090d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876349"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="f09f3-102">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="f09f3-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="f09f3-103">SQL Server 2005, ortak dil çalışma zamanı (CLR) bileşeni .NET Framework'ün tümleştirme Microsoft Windows için kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="f09f3-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="f09f3-104">Bu, saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı türler, kullanıcı tarafından tanımlanan İşlevler, kullanıcı tanımlı toplamları ve akış tablo değerli işlevler, Microsoft Visual Basic .NET ve Microsoft da dahil olmak üzere, herhangi bir .NET Framework dili kullanarak yazabildiğinizi anlamına gelir. Visual C#.</span><span class="sxs-lookup"><span data-stu-id="f09f3-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="f09f3-105"><xref:Microsoft.SqlServer.Server> Ad alanı, yönetilen kod Microsoft SQL Server ortamı ile etkileşimde bulunmasını yeni uygulama programlama arabirimleri (API) kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f09f3-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="f09f3-106">Bu bölümde, özellikler ve SQL Server ortak dil çalışma zamanı (CLR) tümleştirmesini ve SQL Server işlem içi belirli uzantılar ADO.NET özgü davranışları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f09f3-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="f09f3-107">Bu bölümde, SQL Server CLR Tümleştirmesi ile programlamaya başlamak için yeterli bilgi yalnızca sağlamaya yöneliktir ve kapsamlı olacak şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f09f3-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="f09f3-108">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="f09f3-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="f09f3-109">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="f09f3-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="f09f3-110">Ortak dil çalışma zamanı (CLR) tümleştirme programlama kavramları</span><span class="sxs-lookup"><span data-stu-id="f09f3-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="f09f3-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f09f3-111">In This Section</span></span>  
 [<span data-ttu-id="f09f3-112">SQL Server CLR Tümleştirmesine Giriş</span><span class="sxs-lookup"><span data-stu-id="f09f3-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="f09f3-113">SQL Server CLR tümleştirmesine giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="f09f3-114">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f09f3-115">Kullanıcı Tanımlı CLR İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f09f3-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="f09f3-116">Uygulamak ve çeşitli CLR işlevleri kullanmak nasıl açıklar: Tablo değerli, skaler ve kullanıcı tanımlı toplama işlevleri.</span><span class="sxs-lookup"><span data-stu-id="f09f3-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="f09f3-117">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="f09f3-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="f09f3-118">Uygulama ve kullanıcı tanımlı CLR türlerini kullanan açıklar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="f09f3-119">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f09f3-120">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="f09f3-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="f09f3-121">Uygulama ve CLR saklı yordamlar kullanma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f09f3-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="f09f3-122">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f09f3-123">CLR Tetikleyicileri</span><span class="sxs-lookup"><span data-stu-id="f09f3-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="f09f3-124">Uygulama ve CLR Tetikleyicileri kullanma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f09f3-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="f09f3-125">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="f09f3-126">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="f09f3-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="f09f3-127">İçerik Bağlantısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="f09f3-128">SQL Server İşlem İçine Özgü ADO.NET Davranışı</span><span class="sxs-lookup"><span data-stu-id="f09f3-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="f09f3-129">ADO.NET ve içerik bağlantısı için SQL Server işlem içi belirli uzantılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="f09f3-130">Ek konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f09f3-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09f3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f09f3-131">See also</span></span>

- [<span data-ttu-id="f09f3-132">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f09f3-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="f09f3-133">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f09f3-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
