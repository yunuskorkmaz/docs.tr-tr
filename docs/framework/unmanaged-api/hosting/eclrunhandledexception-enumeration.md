---
title: EClrUnhandledException Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 302db0d029b3811d151473323a7a60bd16a00ec1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131242"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="9d01a-102">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9d01a-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="9d01a-103">Kullanıcı kodunda işlenmemiş özel durumları yönetmeye yönelik kullanılabilir seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d01a-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d01a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d01a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="9d01a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9d01a-105">Members</span></span>  
  
|<span data-ttu-id="9d01a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9d01a-106">Member</span></span>|<span data-ttu-id="9d01a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d01a-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="9d01a-108">Varsayılan davranışın oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d01a-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="9d01a-109">İşlem bozulmuş.</span><span class="sxs-lookup"><span data-stu-id="9d01a-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="9d01a-110">Ortak dil çalışma zamanının (CLR) işlenmemiş özel durumları yok saymadığını ve konağın başka bir eylem belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9d01a-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d01a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d01a-111">Remarks</span></span>  
 <span data-ttu-id="9d01a-112">CLR 'nin önceki sürümler gibi davrandığını belirtmek için `eHostDeterminedPolicy` üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d01a-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d01a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d01a-113">Requirements</span></span>  
 <span data-ttu-id="9d01a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d01a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d01a-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d01a-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d01a-116">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d01a-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d01a-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d01a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d01a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d01a-118">See also</span></span>

- [<span data-ttu-id="9d01a-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9d01a-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="9d01a-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9d01a-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="9d01a-121">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d01a-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="9d01a-122">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d01a-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="9d01a-123">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d01a-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="9d01a-124">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9d01a-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
