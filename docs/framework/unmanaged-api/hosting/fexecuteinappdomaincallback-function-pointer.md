---
title: FExecuteInAppDomainCallback İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3de456bc28f51cb20ab72b3934041ec6b06ae
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490447"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="57255-102">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="57255-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="57255-103">Yönetilen kodu yürütmek için ortak dil çalışma zamanı tarafından (CLR) adlı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="57255-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="57255-104">Bu işlev işaretçisi .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="57255-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57255-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57255-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57255-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57255-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="57255-107">[in] Yönetilen kodda yürütülecek içeren donuk arayana ayrılan belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57255-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="57255-108">Ayırma ve yaşam süresini bu bellek (CLR) arayan tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="57255-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="57255-109">CLR Yönetilen yığın bellek değil.</span><span class="sxs-lookup"><span data-stu-id="57255-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57255-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57255-110">Requirements</span></span>  
 <span data-ttu-id="57255-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57255-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57255-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57255-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57255-113">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="57255-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="57255-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57255-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57255-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57255-115">See also</span></span>

- [<span data-ttu-id="57255-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="57255-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
