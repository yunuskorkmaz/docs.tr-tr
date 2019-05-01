---
title: ICorDebugProcess::GetThread Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36070d5374a11daf4b7800481c86d61057989631
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994454"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="80992-102">ICorDebugProcess::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="80992-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="80992-103">Belirtilen işletim sistemi (OS) iş parçacığı kimliği vardır. Bu işlemin iş parçacığı alır</span><span class="sxs-lookup"><span data-stu-id="80992-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80992-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80992-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80992-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80992-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="80992-106">[in] İşletim sistemi iş parçacığı alınacak iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="80992-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="80992-107">[out] İş parçacığını temsil eden bir Icordebugthread nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80992-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80992-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80992-108">Requirements</span></span>  
 <span data-ttu-id="80992-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80992-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80992-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80992-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80992-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80992-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80992-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80992-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
