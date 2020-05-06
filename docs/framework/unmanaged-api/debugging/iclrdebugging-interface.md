---
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
ms.openlocfilehash: a3d4297e3b16dd1637e6293dbf7f04d4fbeda50f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860390"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="e5f74-102">ICLRDebugging Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5f74-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="e5f74-103">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5f74-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5f74-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5f74-104">Methods</span></span>  
  
|<span data-ttu-id="e5f74-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e5f74-105">Method</span></span>|<span data-ttu-id="e5f74-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5f74-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5f74-107">OpenVirtualProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5f74-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="e5f74-108">İşlemde yüklenen ortak dil çalışma zamanı (CLR) modülüne karşılık gelen "ICorDebugProcess" arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="e5f74-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="e5f74-109">CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5f74-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="e5f74-110">Bir [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimi tarafından sağlanmış bir kitaplığın hala kullanımda olup olmadığını veya kaldırılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e5f74-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5f74-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5f74-111">Remarks</span></span>  
 <span data-ttu-id="e5f74-112">Bir `ICLRDebugging` arabirimin örneğini [CLRCreateInstance](../hosting/clrcreateinstance-function.md) işlevini kullanarak elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5f74-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f74-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5f74-113">Requirements</span></span>  
 <span data-ttu-id="e5f74-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5f74-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5f74-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5f74-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5f74-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e5f74-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5f74-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5f74-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f74-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5f74-118">See also</span></span>

- [<span data-ttu-id="e5f74-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e5f74-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e5f74-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e5f74-120">Debugging</span></span>](index.md)
