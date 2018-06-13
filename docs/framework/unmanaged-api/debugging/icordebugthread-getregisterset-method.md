---
title: ICorDebugThread::GetRegisterSet Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc218370779742055e14dc62a8475c42c344c40c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418740"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="a3cb9-102">ICorDebugThread::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="a3cb9-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="a3cb9-103">Bu Icordebugthread nesne etkin bölümü ile ilişkilendirilen kayıt kümesi için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a3cb9-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3cb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3cb9-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3cb9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3cb9-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="a3cb9-106">[out] Adresine bir işaretçi bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) kayıt temsil eden arabirim nesnesi bu iş parçacığının etkin bölümü için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a3cb9-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3cb9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3cb9-107">Requirements</span></span>  
 <span data-ttu-id="a3cb9-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3cb9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3cb9-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3cb9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3cb9-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3cb9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3cb9-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3cb9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
