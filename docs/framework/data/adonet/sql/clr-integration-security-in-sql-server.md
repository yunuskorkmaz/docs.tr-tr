---
title: SQL Server'da CLR tümleştirme güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: dfd99155e42f426eeb01c89c433955cc2e3f0178
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454362"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="4da7b-102">SQL Server'da CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="4da7b-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="4da7b-103">Microsoft SQL Server ortak dil çalışma zamanı (CLR) bileşen .NET Framework'ün tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="4da7b-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="4da7b-104">CLR tümleştirme saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı türler, kullanıcı tarafından tanımlanan İşlevler, kullanıcı tanımlı toplamları ve Microsoft Visual Basic .NET veya Microsoft gibi herhangi bir .NET Framework dili kullanarak akış tablo değerli işlevler yazmanıza olanak sağlar. Visual C#.</span><span class="sxs-lookup"><span data-stu-id="4da7b-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="4da7b-105">CLR, yönetilen kod için kod erişimi güvenliği (CAS) adlı bir güvenlik modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="4da7b-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="4da7b-106">Bu modelde, kod meta verileri tarafından sağlanan kanıt göre derlemelere izinleri verilir.</span><span class="sxs-lookup"><span data-stu-id="4da7b-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="4da7b-107">SQL Server, SQL Server'ın kullanıcı tabanlı güvenlik modeli CLR kod erişim güvenliğini modelle tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="4da7b-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="4da7b-108">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4da7b-108">External Resources</span></span>  
 <span data-ttu-id="4da7b-109">SQL Server ile CLR tümleştirmesi hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="4da7b-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="4da7b-110">Kaynak</span><span class="sxs-lookup"><span data-stu-id="4da7b-110">Resource</span></span>|<span data-ttu-id="4da7b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4da7b-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="4da7b-112">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="4da7b-112">Code Access Security</span></span>](../../../../../docs/framework/misc/code-access-security.md)|<span data-ttu-id="4da7b-113">.NET Framework'teki CAS açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="4da7b-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="4da7b-114">CLR tümleştirme güvenliği</span><span class="sxs-lookup"><span data-stu-id="4da7b-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="4da7b-115">Yönetilen kod içinde SQL Server çalıştırmak için güvenlik modeli açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4da7b-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4da7b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4da7b-116">See Also</span></span>  
 [<span data-ttu-id="4da7b-117">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="4da7b-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="4da7b-118">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="4da7b-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="4da7b-119">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="4da7b-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [<span data-ttu-id="4da7b-120">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4da7b-120">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
