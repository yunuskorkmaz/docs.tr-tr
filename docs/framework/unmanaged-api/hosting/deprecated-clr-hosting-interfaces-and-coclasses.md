---
title: Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 08e193ed40c6538b62d8b1af0a8c41b4225f136b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138256"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="434bb-102">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="434bb-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="434bb-103">Bu bölümde, yönetilmeyen ana bilgisayarların 1,0 ve 1,1 .NET Framework sürümlerindeki ortak dil çalışma zamanını (CLR), uygulamalarına bütünleştirmek için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="434bb-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="434bb-104">Bu arabirimler, bir ana bilgisayarın çalışma zamanını yapılandırmak ve bir işleme yüklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="434bb-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="434bb-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="434bb-105">In This Section</span></span>  
 <span data-ttu-id="434bb-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="434bb-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="434bb-107"><xref:System.AppDomain>yapılandırılacak konak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="434bb-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="434bb-108">ICeeFileGen Sınıfı</span><span class="sxs-lookup"><span data-stu-id="434bb-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="434bb-109">Kullanım dışı Yerel bir Taşınabilir çalıştırılabilir (PE) dosyası oluşturmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="434bb-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="434bb-110">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="434bb-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="434bb-111">CLR ayarlarını yapılandırmak için ana bilgisayar için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="434bb-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="434bb-112">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="434bb-112">Related Sections</span></span>  
 [<span data-ttu-id="434bb-113">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="434bb-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="434bb-114">.NET Framework sürüm 2,0 ve sonraki sürümlerle birlikte sunulan barındırma arabirimlerini tanımlayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="434bb-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
