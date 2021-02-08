---
description: 'Daha fazla bilgi edinin: kullanım dışı CLR barındırma arabirimleri ve coclasses'
title: Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 3d5e8d545dadb4f84c29e2e03a6b23e3729bfe66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785646"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="37700-103">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="37700-103">Deprecated CLR Hosting Interfaces and Coclasses</span></span>

<span data-ttu-id="37700-104">Bu bölümde, yönetilmeyen ana bilgisayarların 1,0 ve 1,1 .NET Framework sürümlerindeki ortak dil çalışma zamanını (CLR), uygulamalarına bütünleştirmek için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37700-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="37700-105">Bu arabirimler, bir ana bilgisayarın çalışma zamanını yapılandırmak ve bir işleme yüklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="37700-105">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37700-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="37700-106">In This Section</span></span>  

 <span data-ttu-id="37700-107">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="37700-107">IAppDomainSetup</span></span>  
 <span data-ttu-id="37700-108">Konağı yapılandırmak için yöntemler sağlar <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="37700-108">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="37700-109">ICeeFileGen Sınıfı</span><span class="sxs-lookup"><span data-stu-id="37700-109">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="37700-110">Kullanım dışı Yerel bir Taşınabilir çalıştırılabilir (PE) dosyası oluşturmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="37700-110">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="37700-111">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37700-111">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="37700-112">CLR ayarlarını yapılandırmak için ana bilgisayar için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="37700-112">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37700-113">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="37700-113">Related Sections</span></span>  

 [<span data-ttu-id="37700-114">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37700-114">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="37700-115">.NET Framework sürüm 2,0 ve sonraki sürümlerle birlikte sunulan barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="37700-115">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
