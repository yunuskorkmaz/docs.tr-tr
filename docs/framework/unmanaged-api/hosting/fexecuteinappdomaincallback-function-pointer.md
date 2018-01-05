---
title: "FExecuteInAppDomainCallback İşlev İşaretçisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FExecuteInAppDomainCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FExecuteInAppDomainCallback
helpviewer_keywords: FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9852abbf2f69dda5c4c3b06f48adbd1bc33f5a1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="bad92-102">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="bad92-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="bad92-103">Yönetilen kod yürütmek için ortak dil çalışma zamanı tarafından (CLR) adlı bir işlev noktalarına.</span><span class="sxs-lookup"><span data-stu-id="bad92-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="bad92-104">Bu işlev işaretçisi kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bad92-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bad92-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bad92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bad92-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="bad92-107">[in] Yürütülecek yönetilen kod içeren donuk çağıran ayrılmış bellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bad92-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="bad92-108">Ayırma ve bu bellek ömrü (CLR) çağıran tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="bad92-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="bad92-109">Bu CLR Yönetilen yığın bellek değildir.</span><span class="sxs-lookup"><span data-stu-id="bad92-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bad92-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bad92-110">Requirements</span></span>  
 <span data-ttu-id="bad92-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bad92-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad92-112">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bad92-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bad92-113">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="bad92-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="bad92-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad92-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad92-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bad92-115">See Also</span></span>  
 [<span data-ttu-id="bad92-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bad92-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
