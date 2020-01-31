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
ms.openlocfilehash: 6b1ccffa4f24122e643a64270f44945afdbc8fff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792645"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="bd706-102">ICorDebugProcess::EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd706-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="bd706-103">Günlük iletilerinin hata ayıklayıcıya aktarılmasını sağlar ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="bd706-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd706-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd706-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd706-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd706-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="bd706-106">[in] `true` günlük iletilerinin iletimini sunar; `false`, iletimi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="bd706-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd706-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd706-107">Remarks</span></span>  
 <span data-ttu-id="bd706-108">Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi oluştuktan sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bd706-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd706-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd706-109">Requirements</span></span>  
 <span data-ttu-id="bd706-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd706-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd706-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bd706-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd706-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bd706-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd706-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd706-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
