---
description: ': ICorDebugNativeFrame:: GetRegisterSet Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8878c438ad76b1a87429e09b8a4a8bbffb90d00d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722418"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="ea6f5-103">ICorDebugNativeFrame::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="ea6f5-103">ICorDebugNativeFrame::GetRegisterSet Method</span></span>

<span data-ttu-id="ea6f5-104">Bu yığın çerçevesi için kayıt kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="ea6f5-104">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea6f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea6f5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea6f5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea6f5-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="ea6f5-107">dışı Bu yığın çerçevesi için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ea6f5-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea6f5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea6f5-108">Requirements</span></span>  

 <span data-ttu-id="ea6f5-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea6f5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea6f5-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea6f5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea6f5-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea6f5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea6f5-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea6f5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea6f5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea6f5-113">See also</span></span>
