---
description: ': ICorDebugThread:: GetUserState metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b63b474525534f9e934954ebe660691db90b8b67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658873"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="c23d0-103">ICorDebugThread::GetUserState Metodu</span><span class="sxs-lookup"><span data-stu-id="c23d0-103">ICorDebugThread::GetUserState Method</span></span>

<span data-ttu-id="c23d0-104">Bu ICorDebugThread 'in geçerli kullanıcı durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="c23d0-104">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c23d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c23d0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c23d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c23d0-106">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="c23d0-107">dışı Bu iş parçacığının geçerli kullanıcı durumunu tanımlayan, CorDebugUserState numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c23d0-107">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c23d0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c23d0-108">Remarks</span></span>  

 <span data-ttu-id="c23d0-109">İş parçacığının kullanıcı durumu, hata ayıklamakta olan program tarafından incelenmekte olan iş parçacığının durumudur.</span><span class="sxs-lookup"><span data-stu-id="c23d0-109">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="c23d0-110">Bir iş parçacığında birden fazla durum bitleri ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="c23d0-110">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c23d0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c23d0-111">Requirements</span></span>  

 <span data-ttu-id="c23d0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c23d0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c23d0-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c23d0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c23d0-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c23d0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c23d0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c23d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
