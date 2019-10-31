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
ms.openlocfilehash: 01c7cb2e4359a477c26f995602dbf29668e567c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131017"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="27b13-102">ICorDebugILFrame::GetArgument Metodu</span><span class="sxs-lookup"><span data-stu-id="27b13-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="27b13-103">Bu Microsoft ara dili (MSIL) yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="27b13-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27b13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27b13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27b13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27b13-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="27b13-106">'ndaki Bu MSIL yığın çerçevesindeki bağımsız değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="27b13-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="27b13-107">dışı Alınan değeri temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27b13-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27b13-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27b13-108">Remarks</span></span>  
 <span data-ttu-id="27b13-109">`GetArgument` yöntemi bir MSIL yığın çerçevesinde veya tam zamanında (JıT) derlenmiş çerçevede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27b13-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27b13-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27b13-110">Requirements</span></span>  
 <span data-ttu-id="27b13-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27b13-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27b13-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="27b13-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27b13-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="27b13-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27b13-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27b13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
