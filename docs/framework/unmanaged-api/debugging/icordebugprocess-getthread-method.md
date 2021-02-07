---
description: ': ICorDebugProcess:: GetThread metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bd636df50afd3f12901c1b48559c44ac6ad0cb81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746912"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="1cd0a-103">ICorDebugProcess::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="1cd0a-103">ICorDebugProcess::GetThread Method</span></span>

<span data-ttu-id="1cd0a-104">Belirtilen işletim sistemi (OS) iş parçacığı KIMLIĞINE sahip bu işlemin iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="1cd0a-104">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd0a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cd0a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cd0a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cd0a-106">Parameters</span></span>  

 `dwThreadId`  
 <span data-ttu-id="1cd0a-107">'ndaki Alınacak iş parçacığının işletim sistemi iş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1cd0a-107">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="1cd0a-108">dışı İş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cd0a-108">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cd0a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cd0a-109">Requirements</span></span>  

 <span data-ttu-id="1cd0a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cd0a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cd0a-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1cd0a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cd0a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1cd0a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cd0a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cd0a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
