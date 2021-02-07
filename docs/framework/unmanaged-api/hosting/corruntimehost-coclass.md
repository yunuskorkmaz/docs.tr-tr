---
description: "Daha fazla bilgi edinin: CorRuntimeHost coclass 'ı"
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
ms.openlocfilehash: cd2d01075e5c8264337e1e989b3d9fdc6bf68962
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760648"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="bc4be-103">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="bc4be-103">CorRuntimeHost Coclass</span></span>

<span data-ttu-id="bc4be-104">Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4be-104">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc4be-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc4be-105">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="bc4be-106">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bc4be-106">Interfaces</span></span>  
  
|<span data-ttu-id="bc4be-107">Arabirim</span><span class="sxs-lookup"><span data-stu-id="bc4be-107">Interface</span></span>|<span data-ttu-id="bc4be-108">Description</span><span class="sxs-lookup"><span data-stu-id="bc4be-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="bc4be-109">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc4be-109">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="bc4be-110">Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4be-110">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="bc4be-111">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc4be-111">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="bc4be-112">Ana bilgisayarın ortak dil çalışma zamanını başlatma ve durdurma, varsayılan etki alanına erişme ve işlemde çalışan tüm etki alanlarını listeleme gibi yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4be-112">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="bc4be-113">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc4be-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="bc4be-114">Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4be-114">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="bc4be-115">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc4be-115">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="bc4be-116">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4be-116">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="bc4be-117">IValidator</span><span class="sxs-lookup"><span data-stu-id="bc4be-117">"IValidator"</span></span>|<span data-ttu-id="bc4be-118">Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4be-118">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc4be-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc4be-119">Requirements</span></span>  

 <span data-ttu-id="bc4be-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc4be-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc4be-121">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="bc4be-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="bc4be-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bc4be-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc4be-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc4be-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4be-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc4be-124">See also</span></span>

- [<span data-ttu-id="bc4be-125">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="bc4be-125">Hosting Coclasses</span></span>](hosting-coclasses.md)
