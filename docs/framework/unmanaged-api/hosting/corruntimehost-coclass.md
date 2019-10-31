---
title: CorRuntimeHost Ortak Sınıfı
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136903"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="a08a1-102">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="a08a1-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="a08a1-103">Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a08a1-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a08a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a08a1-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="a08a1-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a08a1-105">Interfaces</span></span>  
  
|<span data-ttu-id="a08a1-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="a08a1-106">Interface</span></span>|<span data-ttu-id="a08a1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a08a1-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a08a1-108">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a08a1-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="a08a1-109">Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a08a1-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="a08a1-110">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a08a1-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="a08a1-111">Ana bilgisayarın ortak dil çalışma zamanını başlatma ve durdurma, varsayılan etki alanına erişme ve işlemde çalışan tüm etki alanlarını listeleme gibi yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a08a1-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="a08a1-112">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a08a1-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="a08a1-113">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a08a1-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="a08a1-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a08a1-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="a08a1-115">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a08a1-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="a08a1-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="a08a1-116">"IValidator"</span></span>|<span data-ttu-id="a08a1-117">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a08a1-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a08a1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a08a1-118">Requirements</span></span>  
 <span data-ttu-id="a08a1-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a08a1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a08a1-120">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="a08a1-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a08a1-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a08a1-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a08a1-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a08a1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08a1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a08a1-123">See also</span></span>

- [<span data-ttu-id="a08a1-124">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="a08a1-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
