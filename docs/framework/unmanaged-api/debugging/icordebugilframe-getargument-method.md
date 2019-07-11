---
title: ICorDebugILFrame::GetArgument Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e9f627f1ba213f663f042d1107afd1eb05b56b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757869"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="94f81-102">ICorDebugILFrame::GetArgument Metodu</span><span class="sxs-lookup"><span data-stu-id="94f81-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="94f81-103">Bu Microsoft Ara dili (MSIL) yığın çerçevesi içinde belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="94f81-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94f81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94f81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94f81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94f81-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="94f81-106">[in] Bu MSIL yığın çerçevesinde bağımsız değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="94f81-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="94f81-107">[out] Alınan değeri temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94f81-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94f81-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94f81-108">Remarks</span></span>  
 <span data-ttu-id="94f81-109">`GetArgument` Bir MSIL yığın çerçevesinde veya just-in-time (JIT) derlenmiş çerçevesinde yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94f81-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94f81-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94f81-110">Requirements</span></span>  
 <span data-ttu-id="94f81-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94f81-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94f81-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94f81-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94f81-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94f81-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94f81-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94f81-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
