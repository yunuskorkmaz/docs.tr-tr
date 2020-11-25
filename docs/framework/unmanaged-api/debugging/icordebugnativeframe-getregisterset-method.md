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
ms.openlocfilehash: 945a398d32b50efc81ba45e705ed9d4161ed1524
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709277"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="ab52c-102">ICorDebugNativeFrame::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="ab52c-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>

<span data-ttu-id="ab52c-103">Bu yığın çerçevesi için kayıt kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="ab52c-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab52c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ab52c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab52c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab52c-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="ab52c-106">dışı Bu yığın çerçevesi için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab52c-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab52c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab52c-107">Requirements</span></span>  

 <span data-ttu-id="ab52c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab52c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab52c-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab52c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab52c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ab52c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab52c-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab52c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab52c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab52c-112">See also</span></span>
