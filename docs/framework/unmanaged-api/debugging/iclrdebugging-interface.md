---
description: ': ICLRDebugging arabirimi hakkında daha fazla bilgi edinin'
title: ICLRDebugging Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 647b6f7634ef3b9f6ec6080aaff19476c027952a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723345"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="62d2e-103">ICLRDebugging Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62d2e-103">ICLRDebugging Interface</span></span>

<span data-ttu-id="62d2e-104">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="62d2e-104">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62d2e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="62d2e-105">Methods</span></span>  
  
|<span data-ttu-id="62d2e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="62d2e-106">Method</span></span>|<span data-ttu-id="62d2e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62d2e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62d2e-108">OpenVirtualProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62d2e-108">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="62d2e-109">İşlemde yüklenen ortak dil çalışma zamanı (CLR) modülüne karşılık gelen "ICorDebugProcess" arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="62d2e-109">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="62d2e-110">CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62d2e-110">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="62d2e-111">Bir [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimi tarafından sağlanmış bir kitaplığın hala kullanımda olup olmadığını veya kaldırılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="62d2e-111">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62d2e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62d2e-112">Remarks</span></span>  

 <span data-ttu-id="62d2e-113">Bir `ICLRDebugging` arabirimin örneğini [CLRCreateInstance](../hosting/clrcreateinstance-function.md) işlevini kullanarak elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d2e-113">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d2e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62d2e-114">Requirements</span></span>  

 <span data-ttu-id="62d2e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62d2e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d2e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62d2e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62d2e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="62d2e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62d2e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d2e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d2e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62d2e-119">See also</span></span>

- [<span data-ttu-id="62d2e-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="62d2e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="62d2e-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="62d2e-121">Debugging</span></span>](index.md)
