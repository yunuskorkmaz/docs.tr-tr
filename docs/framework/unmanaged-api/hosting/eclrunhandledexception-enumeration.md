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
ms.workload: dotnet
ms.openlocfilehash: a8fcc9254499724d94153c445943fdaf78d12a10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="ebaad-102">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ebaad-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="ebaad-103">Kullanıcı kodunda işlenmeyen özel durumları yönetmek için kullanılabilir seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ebaad-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebaad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebaad-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="ebaad-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ebaad-105">Members</span></span>  
  
|<span data-ttu-id="ebaad-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ebaad-106">Member</span></span>|<span data-ttu-id="ebaad-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebaad-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="ebaad-108">Varsayılan davranış gerçekleşeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebaad-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="ebaad-109">İşlem olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ebaad-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="ebaad-110">Ortak dil çalışma zamanı (CLR) işlenmeyen özel durumlar yoksayar ve başka bir eylem belirlemek konak sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebaad-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebaad-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebaad-111">Remarks</span></span>  
 <span data-ttu-id="ebaad-112">CLR önceki sürümleri gibi davranır belirtmek için kullanın `eHostDeterminedPolicy` üyesi.</span><span class="sxs-lookup"><span data-stu-id="ebaad-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebaad-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebaad-113">Requirements</span></span>  
 <span data-ttu-id="ebaad-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebaad-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebaad-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebaad-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebaad-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebaad-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebaad-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebaad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebaad-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebaad-118">See Also</span></span>  
 [<span data-ttu-id="ebaad-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ebaad-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="ebaad-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ebaad-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="ebaad-121">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebaad-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="ebaad-122">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebaad-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="ebaad-123">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebaad-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="ebaad-124">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ebaad-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
