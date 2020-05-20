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
ms.openlocfilehash: fe378307ce2bda6e1a267e46433ead70a0e2299e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616532"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="c2e3f-102">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="c2e3f-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="c2e3f-103">Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e3f-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2e3f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c2e3f-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="c2e3f-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="c2e3f-105">Interfaces</span></span>  
  
|<span data-ttu-id="c2e3f-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="c2e3f-106">Interface</span></span>|<span data-ttu-id="c2e3f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2e3f-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c2e3f-108">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2e3f-108">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="c2e3f-109">Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e3f-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="c2e3f-110">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2e3f-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="c2e3f-111">Ana bilgisayarın ortak dil çalışma zamanını başlatma ve durdurma, varsayılan etki alanına erişme ve işlemde çalışan tüm etki alanlarını listeleme gibi yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e3f-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="c2e3f-112">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2e3f-112">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="c2e3f-113">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e3f-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="c2e3f-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2e3f-114">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="c2e3f-115">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e3f-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="c2e3f-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="c2e3f-116">"IValidator"</span></span>|<span data-ttu-id="c2e3f-117">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e3f-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2e3f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2e3f-118">Requirements</span></span>  
 <span data-ttu-id="c2e3f-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2e3f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2e3f-120">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="c2e3f-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c2e3f-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c2e3f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2e3f-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2e3f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e3f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2e3f-123">See also</span></span>

- [<span data-ttu-id="c2e3f-124">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="c2e3f-124">Hosting Coclasses</span></span>](hosting-coclasses.md)
