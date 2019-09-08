---
title: SQL Server’da CLR Tümleştirme Güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794563"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="37e89-102">SQL Server’da CLR Tümleştirme Güvenliği</span><span class="sxs-lookup"><span data-stu-id="37e89-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="37e89-103">Microsoft SQL Server, .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="37e89-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="37e89-104">CLR tümleştirmesi saklı yordamlar, Tetikleyiciler, Kullanıcı tanımlı türler, Kullanıcı tanımlı işlevler, Kullanıcı tanımlı toplamalar ve akış tablo değerli işlevler, Microsoft Visual Basic .NET veya Microsoft gibi herhangi bir .NET Framework dil kullanarak yazmanızı sağlar. Görsel C#.</span><span class="sxs-lookup"><span data-stu-id="37e89-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="37e89-105">CLR, yönetilen kod için kod erişim güvenliği (CAS) adlı bir güvenlik modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="37e89-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="37e89-106">Bu modelde, meta verilerde kodun sağladığı kanıtları temel alan derlemelere izinler verilir.</span><span class="sxs-lookup"><span data-stu-id="37e89-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="37e89-107">SQL Server, SQL Server Kullanıcı tabanlı güvenlik modelini CLR 'nin kod erişim tabanlı güvenlik modeliyle tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="37e89-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="37e89-108">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="37e89-108">External Resources</span></span>  
 <span data-ttu-id="37e89-109">SQL Server ile CLR tümleştirmesi hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="37e89-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="37e89-110">Kaynak</span><span class="sxs-lookup"><span data-stu-id="37e89-110">Resource</span></span>|<span data-ttu-id="37e89-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37e89-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="37e89-112">Kod erişim güvenliği</span><span class="sxs-lookup"><span data-stu-id="37e89-112">Code Access Security</span></span>](../../../misc/code-access-security.md)|<span data-ttu-id="37e89-113">.NET Framework CA 'ları açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="37e89-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="37e89-114">CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="37e89-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="37e89-115">SQL Server içinde yürütülen yönetilen kod için güvenlik modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="37e89-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37e89-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37e89-116">See also</span></span>

- [<span data-ttu-id="37e89-117">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="37e89-117">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="37e89-118">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="37e89-118">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="37e89-119">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="37e89-119">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="37e89-120">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="37e89-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
