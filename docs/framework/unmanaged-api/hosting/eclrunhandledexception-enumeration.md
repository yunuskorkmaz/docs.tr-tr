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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba0c2ea7733f098b7fac95f51b5eb16d083174e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779372"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="36fd7-102">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="36fd7-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="36fd7-103">Kullanıcı kodunda işlenmemiş özel durumlar yönetmek için kullanılabilir seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36fd7-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36fd7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36fd7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="36fd7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="36fd7-105">Members</span></span>  
  
|<span data-ttu-id="36fd7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="36fd7-106">Member</span></span>|<span data-ttu-id="36fd7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36fd7-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="36fd7-108">Varsayılan çalışma biçimi oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="36fd7-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="36fd7-109">İşlem bozuk.</span><span class="sxs-lookup"><span data-stu-id="36fd7-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="36fd7-110">Ortak dil çalışma zamanı (CLR) işlenmeyen özel durumlarını yoksayar ve başka bir eylem belirlemek sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="36fd7-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36fd7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36fd7-111">Remarks</span></span>  
 <span data-ttu-id="36fd7-112">CLR önceki sürümleri gibi davrandığından emin belirtmek için kullanın `eHostDeterminedPolicy` üyesi.</span><span class="sxs-lookup"><span data-stu-id="36fd7-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36fd7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36fd7-113">Requirements</span></span>  
 <span data-ttu-id="36fd7-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36fd7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36fd7-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36fd7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36fd7-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36fd7-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36fd7-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36fd7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36fd7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36fd7-118">See also</span></span>

- [<span data-ttu-id="36fd7-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="36fd7-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="36fd7-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="36fd7-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="36fd7-121">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36fd7-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="36fd7-122">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36fd7-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="36fd7-123">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36fd7-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="36fd7-124">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="36fd7-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
