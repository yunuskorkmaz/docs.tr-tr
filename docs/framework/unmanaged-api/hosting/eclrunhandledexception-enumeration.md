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
ms.openlocfilehash: 63b07dda2293d3e05bd3c8fcdc45f20a498ea54c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616313"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="9a6d0-102">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9a6d0-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="9a6d0-103">Kullanıcı kodunda işlenmemiş özel durumları yönetmeye yönelik kullanılabilir seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a6d0-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a6d0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9a6d0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="9a6d0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9a6d0-105">Members</span></span>  
  
|<span data-ttu-id="9a6d0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9a6d0-106">Member</span></span>|<span data-ttu-id="9a6d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a6d0-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="9a6d0-108">Varsayılan davranışın oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a6d0-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="9a6d0-109">İşlem bozulmuş.</span><span class="sxs-lookup"><span data-stu-id="9a6d0-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="9a6d0-110">Ortak dil çalışma zamanının (CLR) işlenmemiş özel durumları yok saymadığını ve konağın başka bir eylem belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9a6d0-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a6d0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a6d0-111">Remarks</span></span>  
 <span data-ttu-id="9a6d0-112">CLR 'nin önceki sürümler gibi davrandığını belirtmek için, üyesini kullanın `eHostDeterminedPolicy` .</span><span class="sxs-lookup"><span data-stu-id="9a6d0-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a6d0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a6d0-113">Requirements</span></span>  
 <span data-ttu-id="9a6d0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a6d0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a6d0-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a6d0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a6d0-116">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a6d0-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a6d0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a6d0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6d0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a6d0-118">See also</span></span>

- [<span data-ttu-id="9a6d0-119">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9a6d0-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="9a6d0-120">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9a6d0-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="9a6d0-121">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a6d0-121">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="9a6d0-122">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a6d0-122">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="9a6d0-123">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a6d0-123">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="9a6d0-124">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9a6d0-124">Hosting Enumerations</span></span>](hosting-enumerations.md)
