---
title: ICorDebugModule::GetSize Metodu
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
ms.openlocfilehash: f0d741bda5426dee1292df0e6fd9107cc2f44c8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413325"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="d7a78-102">ICorDebugModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="d7a78-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="d7a78-103">Modül bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="d7a78-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a78-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7a78-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7a78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7a78-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="d7a78-106">[out] Modül bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d7a78-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="d7a78-107">Modülün yerel Görüntü Oluşturucu (NGen.exe) oluşturduysa modül boyutu sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="d7a78-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a78-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7a78-108">Requirements</span></span>  
 <span data-ttu-id="d7a78-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7a78-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7a78-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7a78-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7a78-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7a78-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7a78-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7a78-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
