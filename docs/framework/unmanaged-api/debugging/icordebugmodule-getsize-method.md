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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46ee21a9fd7b9267672a14107c1706af5d5cdcc5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763574"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="93978-102">ICorDebugModule::GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93978-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="93978-103">Modül bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="93978-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93978-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93978-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93978-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93978-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="93978-106">[out] Modül bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="93978-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="93978-107">Modülün yerel Görüntü Oluşturucu (NGen.exe) vermediyse, modül boyutu sıfır olacaktır.</span><span class="sxs-lookup"><span data-stu-id="93978-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93978-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93978-108">Requirements</span></span>  
 <span data-ttu-id="93978-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93978-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93978-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93978-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93978-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93978-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93978-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93978-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
