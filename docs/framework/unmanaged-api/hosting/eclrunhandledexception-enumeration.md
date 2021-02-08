---
description: 'Daha fazla bilgi edinin: EClrUnhandledException numaralandırması'
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
ms.openlocfilehash: 088d448a92c4d9030208537b9c788477c85f9d37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785555"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="73b1a-103">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="73b1a-103">EClrUnhandledException Enumeration</span></span>

<span data-ttu-id="73b1a-104">Kullanıcı kodunda işlenmemiş özel durumları yönetmeye yönelik kullanılabilir seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="73b1a-104">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b1a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="73b1a-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="73b1a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="73b1a-106">Members</span></span>  
  
|<span data-ttu-id="73b1a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="73b1a-107">Member</span></span>|<span data-ttu-id="73b1a-108">Description</span><span class="sxs-lookup"><span data-stu-id="73b1a-108">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="73b1a-109">Varsayılan davranışın oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="73b1a-109">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="73b1a-110">İşlem bozulmuş.</span><span class="sxs-lookup"><span data-stu-id="73b1a-110">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="73b1a-111">Ortak dil çalışma zamanının (CLR) işlenmemiş özel durumları yok saymadığını ve konağın başka bir eylem belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="73b1a-111">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73b1a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73b1a-112">Remarks</span></span>  

 <span data-ttu-id="73b1a-113">CLR 'nin önceki sürümler gibi davrandığını belirtmek için, üyesini kullanın `eHostDeterminedPolicy` .</span><span class="sxs-lookup"><span data-stu-id="73b1a-113">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73b1a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73b1a-114">Requirements</span></span>  

 <span data-ttu-id="73b1a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73b1a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b1a-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="73b1a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73b1a-117">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73b1a-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73b1a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73b1a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b1a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73b1a-119">See also</span></span>

- [<span data-ttu-id="73b1a-120">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="73b1a-120">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="73b1a-121">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="73b1a-121">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="73b1a-122">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73b1a-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="73b1a-123">SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73b1a-123">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="73b1a-124">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73b1a-124">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="73b1a-125">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="73b1a-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
