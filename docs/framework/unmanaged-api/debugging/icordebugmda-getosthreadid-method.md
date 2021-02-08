---
description: ': ICorDebugMDA:: GetOSThreadId yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f965585a6e6060a14f0cbc2a80b46124b2751e0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801156"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="83bf8-103">ICorDebugMDA::GetOSThreadId Metodu</span><span class="sxs-lookup"><span data-stu-id="83bf8-103">ICorDebugMDA::GetOSThreadId Method</span></span>

<span data-ttu-id="83bf8-104">[ICorDebugMDA](icordebugmda-interface.md) tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ' nin yürütüldüğü işletim SISTEMI (OS) iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="83bf8-104">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83bf8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83bf8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83bf8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83bf8-106">Parameters</span></span>  

 `pOsTid`  
 <span data-ttu-id="83bf8-107">dışı İşletim sistemi iş parçacığı tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83bf8-107">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83bf8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83bf8-108">Remarks</span></span>  

 <span data-ttu-id="83bf8-109">İşletim sistemi iş parçacığı bir ICorDebugThread yerine, bir MDA 'ın yerel bir iş parçacığında ya da henüz yönetilen kodu girilmemiş yönetilen bir iş parçacığında tetiklenme durumlarına izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="83bf8-109">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83bf8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83bf8-110">Requirements</span></span>  

 <span data-ttu-id="83bf8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83bf8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83bf8-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="83bf8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83bf8-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="83bf8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83bf8-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83bf8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83bf8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83bf8-115">See also</span></span>

- [<span data-ttu-id="83bf8-116">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83bf8-116">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="83bf8-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="83bf8-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
