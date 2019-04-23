---
title: ICorDebugNativeFrame::GetRegisterSet Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a4f7ecc227679e6b0afa29b20de1aefeae3b76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077933"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="d572c-102">ICorDebugNativeFrame::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="d572c-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="d572c-103">Bu yığın çerçevesi için kaydı alır.</span><span class="sxs-lookup"><span data-stu-id="d572c-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d572c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d572c-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d572c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d572c-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="d572c-106">[out] Adresine bir işaretçi bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) kasayı temsil eden nesne bu yığın çerçevesi için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d572c-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d572c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d572c-107">Requirements</span></span>  
 <span data-ttu-id="d572c-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d572c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d572c-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d572c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d572c-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d572c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d572c-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d572c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d572c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d572c-112">See also</span></span>
