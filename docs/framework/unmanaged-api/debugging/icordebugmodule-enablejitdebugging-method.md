---
title: "ICorDebugModule::EnableJITDebugging Yöntemi"
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
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="1f9b3-102">ICorDebugModule::EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f9b3-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="1f9b3-103">Tam zamanında (JIT) derleyici bu modül içinde yöntemleri için hata ayıklama bilgilerini korur olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1f9b3-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f9b3-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f9b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f9b3-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="1f9b3-106">[in] Bu değer ayarlanırsa `true` Microsoft Ara dili (MSIL) ve bu Modülün her bir yöntemin JIT derlenmiş sürümleri arasında eşleme bilgilerini korumak JIT Derleyici etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1f9b3-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="1f9b3-107">[in] Bu değer ayarlanırsa `true` hata ayıklama için belirli JIT özgü en iyi duruma getirme ile kodu oluşturmak JIT Derleyici etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1f9b3-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f9b3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f9b3-108">Remarks</span></span>  
 <span data-ttu-id="1f9b3-109">JIT hata ayıklama hata ayıklayıcısı etkinken yüklenen tüm modülleri için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="1f9b3-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="1f9b3-110">Program aracılığıyla etkinleştirme veya ayarlarını devre dışı bırakma genel ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1f9b3-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f9b3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f9b3-111">Requirements</span></span>  
 <span data-ttu-id="1f9b3-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f9b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f9b3-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f9b3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f9b3-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f9b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f9b3-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f9b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
