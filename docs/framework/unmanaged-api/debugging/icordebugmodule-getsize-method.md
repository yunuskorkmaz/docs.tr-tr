---
description: ': ICorDebugModule:: GetSize yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b2179c8830911e417ccd482fe72438c4cd7fd3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660160"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="ba378-103">ICorDebugModule::GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba378-103">ICorDebugModule::GetSize Method</span></span>

<span data-ttu-id="ba378-104">Modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="ba378-104">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba378-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba378-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba378-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba378-106">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="ba378-107">dışı Modülün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ba378-107">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="ba378-108">Modül yerel görüntü Oluşturucu (NGen.exe) tarafından üretildiyse, modülün boyutu sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="ba378-108">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba378-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba378-109">Requirements</span></span>  

 <span data-ttu-id="ba378-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba378-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba378-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ba378-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba378-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba378-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba378-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba378-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
