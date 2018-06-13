---
title: ICorDebugProcess::EnableLogMessages Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0dbac6570fc0af0452a0e44f838124afbf6a4fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419890"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="e3da5-102">ICorDebugProcess::EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3da5-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="e3da5-103">Hata ayıklayıcı günlük iletilerini iletimini devre dışı bırakır ve sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3da5-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3da5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3da5-104">Syntax</span></span>  
  
```  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3da5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3da5-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="e3da5-106">[in] `true` günlük iletilerini; aktarımını sağlar `false` iletimi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e3da5-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3da5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3da5-107">Remarks</span></span>  
 <span data-ttu-id="e3da5-108">Bu yöntem yalnızca sonra geçerli [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma oluşur.</span><span class="sxs-lookup"><span data-stu-id="e3da5-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3da5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3da5-109">Requirements</span></span>  
 <span data-ttu-id="e3da5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3da5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3da5-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3da5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3da5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3da5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3da5-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3da5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
