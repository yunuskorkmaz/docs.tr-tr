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
ms.openlocfilehash: cd4e675b4ba50b47146428d204c28cc943c23c69
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688009"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="0cab0-102">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="0cab0-102">CorRuntimeHost Coclass</span></span>

<span data-ttu-id="0cab0-103">Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cab0-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cab0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0cab0-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="0cab0-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="0cab0-105">Interfaces</span></span>  
  
|<span data-ttu-id="0cab0-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="0cab0-106">Interface</span></span>|<span data-ttu-id="0cab0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cab0-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="0cab0-108">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cab0-108">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="0cab0-109">Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cab0-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="0cab0-110">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cab0-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="0cab0-111">Ana bilgisayarın ortak dil çalışma zamanını başlatma ve durdurma, varsayılan etki alanına erişme ve işlemde çalışan tüm etki alanlarını listeleme gibi yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cab0-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="0cab0-112">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cab0-112">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="0cab0-113">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cab0-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="0cab0-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cab0-114">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="0cab0-115">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cab0-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="0cab0-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="0cab0-116">"IValidator"</span></span>|<span data-ttu-id="0cab0-117">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cab0-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0cab0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cab0-118">Requirements</span></span>  

 <span data-ttu-id="0cab0-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cab0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cab0-120">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="0cab0-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0cab0-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0cab0-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cab0-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cab0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cab0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cab0-123">See also</span></span>

- [<span data-ttu-id="0cab0-124">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="0cab0-124">Hosting Coclasses</span></span>](hosting-coclasses.md)
