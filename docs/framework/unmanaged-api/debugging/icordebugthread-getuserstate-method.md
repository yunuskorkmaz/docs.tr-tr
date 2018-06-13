---
title: ICorDebugThread::GetUserState Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06ff8f0f13d7710d2d3d59aac4b5fdcadfe707be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418398"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="9a987-102">ICorDebugThread::GetUserState Metodu</span><span class="sxs-lookup"><span data-stu-id="9a987-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="9a987-103">Bu Icordebugthread geçerli kullanıcı durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="9a987-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a987-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a987-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a987-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a987-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="9a987-106">[out] Bu iş parçacığı geçerli kullanıcı durumunu açıklayan CorDebugUserState numaralandırma değerlerinin Bitsel bir birleşimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a987-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a987-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a987-107">Remarks</span></span>  
 <span data-ttu-id="9a987-108">Ayıklanacak program tarafından incelenmesi, kullanıcı durumu iş parçacığının iş parçacığı durumudur.</span><span class="sxs-lookup"><span data-stu-id="9a987-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="9a987-109">Bir iş parçacığı birden fazla durum bitler olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a987-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a987-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a987-110">Requirements</span></span>  
 <span data-ttu-id="9a987-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a987-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a987-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a987-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a987-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a987-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a987-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a987-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
