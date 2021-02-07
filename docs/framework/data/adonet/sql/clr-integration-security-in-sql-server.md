---
description: 'Hakkında daha fazla bilgi edinin SQL Server: CLR tümleştirme güvenliği'
title: SQL Server’da CLR Tümleştirme Güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 5de552c0f5b869712d2038b53abd50b8ded04747
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718544"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="12cc4-103">SQL Server’da CLR Tümleştirme Güvenliği</span><span class="sxs-lookup"><span data-stu-id="12cc4-103">CLR Integration Security in SQL Server</span></span>

<span data-ttu-id="12cc4-104">Microsoft SQL Server, .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="12cc4-104">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="12cc4-105">CLR tümleştirmesi saklı yordamlar, Tetikleyiciler, Kullanıcı tanımlı türler, Kullanıcı tanımlı işlevler, Kullanıcı tanımlı toplamalar ve akış tablo değerli işlevlerini, Microsoft Visual Basic .NET veya Microsoft Visual C# gibi .NET Framework herhangi bir dili kullanarak yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="12cc4-105">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="12cc4-106">CLR, yönetilen kod için kod erişim güvenliği (CAS) adlı bir güvenlik modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="12cc4-106">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="12cc4-107">Bu modelde, meta verilerde kodun sağladığı kanıtları temel alan derlemelere izinler verilir.</span><span class="sxs-lookup"><span data-stu-id="12cc4-107">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="12cc4-108">SQL Server, SQL Server Kullanıcı tabanlı güvenlik modelini CLR 'nin kod erişim tabanlı güvenlik modeliyle tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="12cc4-108">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="12cc4-109">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="12cc4-109">External Resources</span></span>  

 <span data-ttu-id="12cc4-110">SQL Server ile CLR tümleştirmesi hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="12cc4-110">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="12cc4-111">Kaynak</span><span class="sxs-lookup"><span data-stu-id="12cc4-111">Resource</span></span>|<span data-ttu-id="12cc4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12cc4-112">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="12cc4-113">Kod erişim güvenliği</span><span class="sxs-lookup"><span data-stu-id="12cc4-113">Code Access Security</span></span>](../../../misc/code-access-security.md)|<span data-ttu-id="12cc4-114">.NET Framework CA 'ları açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="12cc4-114">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="12cc4-115">CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="12cc4-115">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="12cc4-116">SQL Server içinde yürütülen yönetilen kod için güvenlik modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="12cc4-116">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12cc4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12cc4-117">See also</span></span>

- [<span data-ttu-id="12cc4-118">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="12cc4-118">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="12cc4-119">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="12cc4-119">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="12cc4-120">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="12cc4-120">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="12cc4-121">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="12cc4-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
