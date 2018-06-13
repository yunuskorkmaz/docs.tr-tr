---
title: ICorDebugThread::GetDebugState Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95d9696e29bc1b460c94d7f4d8afd3de82653333
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419636"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="6c869-102">ICorDebugThread::GetDebugState Metodu</span><span class="sxs-lookup"><span data-stu-id="6c869-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="6c869-103">Bu Icordebugthread nesne geçerli hata ayıklama durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="6c869-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c869-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c869-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c869-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c869-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="6c869-106">[out] Bu iş parçacığı geçerli hata ayıklama durumunu açıklayan CorDebugThreadState numaralandırma değerlerinin Bitsel birleşimine gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c869-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c869-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c869-107">Remarks</span></span>  
 <span data-ttu-id="6c869-108">İşlem şu anda durursa, `pState` işlemi devam için bu iş parçacığının gerçek geçerli durumu olsaydı bu iş parçacığı için var olan hata ayıklama durumuna temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c869-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c869-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c869-109">Requirements</span></span>  
 <span data-ttu-id="6c869-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c869-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c869-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c869-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c869-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c869-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c869-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c869-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
