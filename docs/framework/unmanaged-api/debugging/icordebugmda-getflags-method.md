---
title: ICorDebugMDA::GetFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 701d578a1d3af941923d68ddc0cb7c97dd0ca8ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761930"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="a777d-102">ICorDebugMDA::GetFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="a777d-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="a777d-103">Tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ilişkili bayraklar alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a777d-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a777d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a777d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a777d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a777d-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="a777d-106">[in] Bitsel bir birleşimi [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) numaralandırma değerlerinin bayrakları bu mda'nın ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a777d-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a777d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a777d-107">Requirements</span></span>  
 <span data-ttu-id="a777d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a777d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a777d-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a777d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a777d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a777d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a777d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a777d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a777d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a777d-112">See also</span></span>

- [<span data-ttu-id="a777d-113">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a777d-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="a777d-114">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a777d-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
