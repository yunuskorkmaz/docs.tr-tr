---
title: ICorDebugILFrame::GetLocalVariable Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd36f01297f24c050f84fb67e7673f8641fe206
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789733"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="163db-102">ICorDebugILFrame::GetLocalVariable Metodu</span><span class="sxs-lookup"><span data-stu-id="163db-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="163db-103">Bu Microsoft Ara dili (MSIL) yığın çerçevesi içinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="163db-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="163db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="163db-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="163db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="163db-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="163db-106">[in] Bu MSIL yığın çerçevesinde yerel değişken dizini.</span><span class="sxs-lookup"><span data-stu-id="163db-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="163db-107">[out] Alınan değeri temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="163db-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="163db-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="163db-108">Remarks</span></span>  
 <span data-ttu-id="163db-109">`GetLocalVariable` Bir MSIL yığın çerçevesinde veya just-in-time (JIT) derlenmiş çerçevesinde yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="163db-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="163db-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="163db-110">Requirements</span></span>  
 <span data-ttu-id="163db-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="163db-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="163db-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="163db-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="163db-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="163db-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="163db-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="163db-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
