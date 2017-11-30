---
title: "EClrUnhandledException Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrUnhandledException
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrUnhandledException
helpviewer_keywords: EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67787072779e0cb22a339c2d13c972ba36f3ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="8a760-102">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8a760-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="8a760-103">Kullanıcı kodunda işlenmeyen özel durumları yönetmek için kullanılabilir seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a760-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a760-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a760-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="8a760-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8a760-105">Members</span></span>  
  
|<span data-ttu-id="8a760-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8a760-106">Member</span></span>|<span data-ttu-id="8a760-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a760-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="8a760-108">Varsayılan davranış gerçekleşeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a760-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="8a760-109">İşlem olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="8a760-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="8a760-110">Ortak dil çalışma zamanı (CLR) işlenmeyen özel durumlar yoksayar ve başka bir eylem belirlemek konak sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a760-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a760-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a760-111">Remarks</span></span>  
 <span data-ttu-id="8a760-112">CLR önceki sürümleri gibi davranır belirtmek için kullanın `eHostDeterminedPolicy` üyesi.</span><span class="sxs-lookup"><span data-stu-id="8a760-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a760-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a760-113">Requirements</span></span>  
 <span data-ttu-id="8a760-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a760-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a760-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a760-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a760-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a760-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a760-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a760-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a760-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a760-118">See Also</span></span>  
 [<span data-ttu-id="8a760-119">EClrFailure numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8a760-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="8a760-120">EClrOperation numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8a760-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="8a760-121">Iclrpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a760-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="8a760-122">SetUnhandledExceptionPolicy yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a760-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="8a760-123">Ihostpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a760-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="8a760-124">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8a760-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
