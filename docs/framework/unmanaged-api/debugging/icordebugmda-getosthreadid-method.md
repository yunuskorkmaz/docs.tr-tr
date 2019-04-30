---
title: ICorDebugMDA::GetOSThreadId Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51d29fed3d53611daa0042251ce09638399f7ed5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723153"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="61a10-102">ICorDebugMDA::GetOSThreadId Metodu</span><span class="sxs-lookup"><span data-stu-id="61a10-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="61a10-103">Yönetilen hata ayıklama Yardımcısı (MDA) temsil ettiği bağlı işletim sistemi (OS) iş parçacığı tanımlayıcısını alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) yürütüyor.</span><span class="sxs-lookup"><span data-stu-id="61a10-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61a10-104">Syntax</span></span>  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61a10-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61a10-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="61a10-106">[out] İşletim sistemi iş parçacığı tanımlayıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61a10-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61a10-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61a10-107">Remarks</span></span>  
 <span data-ttu-id="61a10-108">İşletim sistemi iş parçacığı bir Icordebugthread yerine bir MDA yerel bir iş parçacığı veya bir yönetilen iş parçacığı henüz yönetilen kod girmedi tetiklenir durumlarda izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="61a10-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a10-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61a10-109">Requirements</span></span>  
 <span data-ttu-id="61a10-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a10-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a10-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61a10-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61a10-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61a10-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61a10-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a10-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a10-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61a10-114">See also</span></span>

- [<span data-ttu-id="61a10-115">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61a10-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="61a10-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="61a10-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
