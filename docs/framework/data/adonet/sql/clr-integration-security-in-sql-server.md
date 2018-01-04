---
title: "SQL Server CLR tümleştirmesi güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: aa211005f13fca2c55ff693a12b3e37629e39ad3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="fd29d-102">SQL Server CLR tümleştirmesi güvenliği</span><span class="sxs-lookup"><span data-stu-id="fd29d-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="fd29d-103">Microsoft SQL Server, .NET Framework ortak dil çalışma zamanı (CLR) bileşeni tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd29d-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="fd29d-104">CLR tümleştirmesi, saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı türler, kullanıcı tanımlı işlevler, kullanıcı tanımlı toplamlarda ve Microsoft Visual Basic .NET ya da Microsoft gibi herhangi bir .NET Framework dil kullanarak akış tablo değerli işlevler yazma sağlar Visual C#.</span><span class="sxs-lookup"><span data-stu-id="fd29d-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="fd29d-105">CLR yönetilen kod için kod erişim güvenliği (CAS) adlı bir güvenlik modeli destekler.</span><span class="sxs-lookup"><span data-stu-id="fd29d-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="fd29d-106">Bu modelde, meta verileri kod tarafından sağlanan bulgu göre derlemeler için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fd29d-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="fd29d-107">SQL Server, SQL Server'ın kullanıcı tabanlı güvenlik modeli CLR kodu erişim tabanlı güvenlik modeli ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="fd29d-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="fd29d-108">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="fd29d-108">External Resources</span></span>  
 <span data-ttu-id="fd29d-109">SQL Server ile CLR tümleştirme hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="fd29d-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="fd29d-110">Kaynak</span><span class="sxs-lookup"><span data-stu-id="fd29d-110">Resource</span></span>|<span data-ttu-id="fd29d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd29d-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="fd29d-112">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="fd29d-112">Code Access Security</span></span>](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="fd29d-113">.NET Framework CA'LARDA açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="fd29d-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="fd29d-114">CLR tümleştirme güvenlik</span><span class="sxs-lookup"><span data-stu-id="fd29d-114">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=59998)|<span data-ttu-id="fd29d-115">Yönetilen kod içinde SQL Server yürütme güvenlik modeli açıklanır.</span><span class="sxs-lookup"><span data-stu-id="fd29d-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd29d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd29d-116">See Also</span></span>  
 [<span data-ttu-id="fd29d-117">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="fd29d-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="fd29d-118">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="fd29d-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="fd29d-119">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="fd29d-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [<span data-ttu-id="fd29d-120">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="fd29d-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
