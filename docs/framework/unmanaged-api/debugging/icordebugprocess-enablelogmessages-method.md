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
ms.openlocfilehash: fe237ca01d409636f184930d26ca970d58e90437
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472958"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="3be27-102">ICorDebugProcess::EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3be27-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="3be27-103">Etkinleştirir ve günlük ileti hata ayıklayıcı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3be27-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3be27-104">Syntax</span></span>  
  
```  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3be27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3be27-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="3be27-106">[in] `true` günlük ileti; sağlar `false` iletimi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3be27-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3be27-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3be27-107">Remarks</span></span>  
 <span data-ttu-id="3be27-108">Bu yöntem yalnızca geçerli [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3be27-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3be27-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3be27-109">Requirements</span></span>  
 <span data-ttu-id="3be27-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3be27-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3be27-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3be27-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3be27-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3be27-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3be27-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3be27-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
