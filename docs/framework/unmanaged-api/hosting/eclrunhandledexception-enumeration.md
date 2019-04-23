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
ms.openlocfilehash: 7e5fb3ab1d2dedb220fd4a486409512414233021
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176676"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="33191-102">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="33191-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="33191-103">Kullanıcı kodunda işlenmemiş özel durumlar yönetmek için kullanılabilir seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33191-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33191-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33191-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="33191-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="33191-105">Members</span></span>  
  
|<span data-ttu-id="33191-106">Üye</span><span class="sxs-lookup"><span data-stu-id="33191-106">Member</span></span>|<span data-ttu-id="33191-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33191-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="33191-108">Varsayılan çalışma biçimi oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="33191-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="33191-109">İşlem bozuk.</span><span class="sxs-lookup"><span data-stu-id="33191-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="33191-110">Ortak dil çalışma zamanı (CLR) işlenmeyen özel durumlarını yoksayar ve başka bir eylem belirlemek sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="33191-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33191-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33191-111">Remarks</span></span>  
 <span data-ttu-id="33191-112">CLR önceki sürümleri gibi davrandığından emin belirtmek için kullanın `eHostDeterminedPolicy` üyesi.</span><span class="sxs-lookup"><span data-stu-id="33191-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33191-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33191-113">Requirements</span></span>  
 <span data-ttu-id="33191-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33191-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33191-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="33191-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33191-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33191-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33191-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33191-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33191-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33191-118">See also</span></span>

- [<span data-ttu-id="33191-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="33191-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="33191-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="33191-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="33191-121">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33191-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="33191-122">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33191-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="33191-123">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33191-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="33191-124">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="33191-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
