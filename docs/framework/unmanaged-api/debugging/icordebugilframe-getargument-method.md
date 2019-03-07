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
ms.openlocfilehash: 46852ed8ac53c3a7720edff4833f3dc3cce42bbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475794"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="17c87-102">ICorDebugILFrame::GetArgument Metodu</span><span class="sxs-lookup"><span data-stu-id="17c87-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="17c87-103">Bu Microsoft Ara dili (MSIL) yığın çerçevesi içinde belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="17c87-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17c87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17c87-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17c87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17c87-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="17c87-106">[in] Bu MSIL yığın çerçevesinde bağımsız değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="17c87-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="17c87-107">[out] Alınan değeri temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="17c87-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17c87-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17c87-108">Remarks</span></span>  
 <span data-ttu-id="17c87-109">`GetArgument` Bir MSIL yığın çerçevesinde veya just-in-time (JIT) derlenmiş çerçevesinde yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="17c87-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17c87-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17c87-110">Requirements</span></span>  
 <span data-ttu-id="17c87-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17c87-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17c87-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17c87-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17c87-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17c87-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17c87-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17c87-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
