---
description: ': ICorDebugProcess:: EnableLogMessages yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d44f1a14611493372c7321feaa14329d5d77b01b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753997"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="3ced3-103">ICorDebugProcess::EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ced3-103">ICorDebugProcess::EnableLogMessages Method</span></span>

<span data-ttu-id="3ced3-104">Günlük iletilerinin hata ayıklayıcıya aktarılmasını sağlar ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3ced3-104">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ced3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ced3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ced3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ced3-106">Parameters</span></span>  

 `fOnOff`  
 <span data-ttu-id="3ced3-107">[in] `true` günlük iletilerinin iletimini sunar; `false` iletimi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3ced3-107">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ced3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ced3-108">Remarks</span></span>  

 <span data-ttu-id="3ced3-109">Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi oluştuktan sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3ced3-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ced3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ced3-110">Requirements</span></span>  

 <span data-ttu-id="3ced3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ced3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ced3-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ced3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ced3-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3ced3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ced3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ced3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
