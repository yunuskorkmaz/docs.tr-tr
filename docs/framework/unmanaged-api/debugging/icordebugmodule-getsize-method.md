---
title: ICorDebugModule::GetSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
ms.openlocfilehash: 0cfc31839b263c2e8cf44d15439b44ffacccf5bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709914"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="d1129-102">ICorDebugModule::GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1129-102">ICorDebugModule::GetSize Method</span></span>

<span data-ttu-id="d1129-103">Modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="d1129-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1129-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d1129-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1129-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1129-105">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="d1129-106">dışı Modülün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d1129-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="d1129-107">Modül yerel görüntü Oluşturucu (NGen.exe) tarafından üretildiyse, modülün boyutu sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="d1129-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1129-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1129-108">Requirements</span></span>  

 <span data-ttu-id="d1129-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1129-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1129-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1129-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1129-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d1129-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1129-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1129-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
