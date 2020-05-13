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
ms.openlocfilehash: 081852f91f243c4a979e2969220e71bd10c8c56b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212897"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="acf82-102">ICorDebugProcess::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="acf82-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="acf82-103">Belirtilen işletim sistemi (OS) iş parçacığı KIMLIĞINE sahip bu işlemin iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="acf82-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acf82-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acf82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acf82-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="acf82-106">'ndaki Alınacak iş parçacığının işletim sistemi iş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="acf82-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="acf82-107">dışı İş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="acf82-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acf82-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acf82-108">Requirements</span></span>  
 <span data-ttu-id="acf82-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acf82-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acf82-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="acf82-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acf82-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acf82-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acf82-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acf82-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
