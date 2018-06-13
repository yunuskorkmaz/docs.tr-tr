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
ms.openlocfilehash: 6880ed3a2519ad7d4a415e4fcc4510668a0852f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416712"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="fe85c-102">ICorDebugNativeFrame::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="fe85c-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="fe85c-103">Bu yığın çerçevesi için kayıt alır.</span><span class="sxs-lookup"><span data-stu-id="fe85c-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe85c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe85c-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe85c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe85c-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="fe85c-106">[out] Adresine bir işaretçi bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) kayıt temsil eden nesne ayarlamak için bu yığın çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="fe85c-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe85c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe85c-107">Requirements</span></span>  
 <span data-ttu-id="fe85c-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe85c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe85c-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe85c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe85c-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe85c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe85c-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe85c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe85c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe85c-112">See Also</span></span>  
 
