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
ms.openlocfilehash: 16608980505ffc03ef8ecc19cacddabaefaba6ca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471751"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="ac697-102">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="ac697-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="ac697-103">Yönetilen kodu yürütmek için ortak dil çalışma zamanı tarafından (CLR) adlı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="ac697-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="ac697-104">Bu işlev işaretçisi içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac697-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac697-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac697-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac697-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac697-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="ac697-107">[in] Yönetilen kodda yürütülecek içeren donuk arayana ayrılan belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac697-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="ac697-108">Ayırma ve yaşam süresini bu bellek (CLR) arayan tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ac697-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="ac697-109">CLR Yönetilen yığın bellek değil.</span><span class="sxs-lookup"><span data-stu-id="ac697-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac697-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac697-110">Requirements</span></span>  
 <span data-ttu-id="ac697-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac697-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac697-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac697-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac697-113">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="ac697-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="ac697-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac697-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac697-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac697-115">See also</span></span>
- [<span data-ttu-id="ac697-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ac697-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
