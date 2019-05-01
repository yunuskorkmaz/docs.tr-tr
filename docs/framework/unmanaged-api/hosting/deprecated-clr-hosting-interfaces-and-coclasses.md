---
title: Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6c20a69894c95086dbd813601ac8811ab4f337
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985705"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="61e77-102">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="61e77-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="61e77-103">Bu bölümde, yönetilmeyen arabirimler açıklanmaktadır. konakları ortak dil çalışma zamanı (CLR) tümleştirme için kullanabileceğiniz .NET Framework sürüm 1.0 ve 1.1 uygulamalarına.</span><span class="sxs-lookup"><span data-stu-id="61e77-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="61e77-104">Bu arabirimler, yapılandırmak ve çalışma zamanını bir işleme yüklemek bir konak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="61e77-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61e77-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="61e77-105">In This Section</span></span>  
 <span data-ttu-id="61e77-106">Iappdomainsetup</span><span class="sxs-lookup"><span data-stu-id="61e77-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="61e77-107">Yapılandırmak konak için yöntemler sağlar bir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="61e77-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="61e77-108">ICeeFileGen Sınıfı</span><span class="sxs-lookup"><span data-stu-id="61e77-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="61e77-109">(Kullanım dışı) Bir yerel taşınabilir yürütülebilir (PE) dosyası oluşturmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="61e77-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="61e77-110">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61e77-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="61e77-111">CLR ayarlarını yapılandırmak konak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="61e77-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="61e77-112">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="61e77-112">Related Sections</span></span>  
 [<span data-ttu-id="61e77-113">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="61e77-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="61e77-114">Barındırma arabirimleri .NET Framework sürüm 2.0 ve sonraki sürümler ile sağlanan açıklayan konulara içerir.</span><span class="sxs-lookup"><span data-stu-id="61e77-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
