---
title: ICorDebugCode2::GetCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df7ecd7403c915df89fe26a0ce9229b88691d19c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667472"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="887f6-102">ICorDebugCode2::GetCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="887f6-102">ICorDebugCode2::GetCompilerFlags Method</span></span>
<span data-ttu-id="887f6-103">Koşullar altında bu kod nesnesi ya da tam derleme ya da yerel Görüntü Oluşturucu (Ngen.exe) kullanılarak oluşturulan zamanında (JIT) olduğu belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="887f6-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="887f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="887f6-104">Syntax</span></span>  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="887f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="887f6-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="887f6-106">[out] Bir işaretçi değerini [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) JIT derleyicisi veya yerel Görüntü Oluşturucu davranışını belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="887f6-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="887f6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="887f6-107">Requirements</span></span>  
 <span data-ttu-id="887f6-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="887f6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="887f6-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="887f6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="887f6-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="887f6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="887f6-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="887f6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887f6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="887f6-112">See also</span></span>

