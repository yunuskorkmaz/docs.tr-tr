---
title: ICorDebugILFrame::GetArgument Metodu
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c6b1c097d830af4e68035f79670983002c15c16d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="f02ac-102">ICorDebugILFrame::GetArgument Metodu</span><span class="sxs-lookup"><span data-stu-id="f02ac-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="f02ac-103">Belirtilen bağımsız değişkenin değeri bu Microsoft Ara dili (MSIL) yığın çerçevesinde bulunan alır.</span><span class="sxs-lookup"><span data-stu-id="f02ac-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f02ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f02ac-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f02ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f02ac-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="f02ac-106">[in] Bu MSIL yığın çerçevesi değişkeninde dizini.</span><span class="sxs-lookup"><span data-stu-id="f02ac-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f02ac-107">[out] Alınan değerin temsil eden Icordebugvalue nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f02ac-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f02ac-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f02ac-108">Remarks</span></span>  
 <span data-ttu-id="f02ac-109">`GetArgument` MSIL yığın çerçevesi veya tam zamanında (JIT) derlenmiş çerçeve yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f02ac-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f02ac-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f02ac-110">Requirements</span></span>  
 <span data-ttu-id="f02ac-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f02ac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f02ac-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f02ac-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f02ac-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f02ac-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f02ac-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f02ac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
