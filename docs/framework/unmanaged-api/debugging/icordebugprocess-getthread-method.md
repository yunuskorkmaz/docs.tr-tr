---
title: ICorDebugProcess::GetThread Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 996003f254c5150dfd39ca62d7cadf07282596c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="786d6-102">ICorDebugProcess::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="786d6-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="786d6-103">Belirtilen işletim sistemi (OS) iş parçacığı kimliği vardır. Bu işlemin iş parçacığı alır</span><span class="sxs-lookup"><span data-stu-id="786d6-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="786d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="786d6-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="786d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="786d6-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="786d6-106">[in] İşletim sistemi iş parçacığı alınması için iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="786d6-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="786d6-107">[out] Bir işaretçi adresine Icordebugthread nesnenin iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="786d6-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="786d6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="786d6-108">Requirements</span></span>  
 <span data-ttu-id="786d6-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="786d6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="786d6-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="786d6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="786d6-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="786d6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="786d6-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="786d6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
