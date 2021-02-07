---
description: ': Icordebugzincirine:: GetRegisterSet Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugChain::GetRegisterSet Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
ms.openlocfilehash: 75c77838cb4ef49dd922a4e39b41e622693e928d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694962"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="69399-103">ICorDebugChain::GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69399-103">ICorDebugChain::GetRegisterSet Method</span></span>

<span data-ttu-id="69399-104">Bu zincirin etkin bölümü için kayıt kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="69399-104">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69399-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69399-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69399-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69399-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="69399-107">dışı Bu zincirin etkin bölümü için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="69399-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69399-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69399-108">Requirements</span></span>  

 <span data-ttu-id="69399-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69399-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69399-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69399-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69399-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="69399-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69399-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69399-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
