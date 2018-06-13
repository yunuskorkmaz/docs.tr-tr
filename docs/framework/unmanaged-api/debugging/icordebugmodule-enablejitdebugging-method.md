---
title: ICorDebugModule::EnableJITDebugging Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71722293bfb80a7e57393916560f922d970ea2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415648"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="f663a-102">ICorDebugModule::EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f663a-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="f663a-103">Tam zamanında (JIT) derleyici bu modül içinde yöntemleri için hata ayıklama bilgilerini korur olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="f663a-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f663a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f663a-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f663a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f663a-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="f663a-106">[in] Bu değer ayarlanırsa `true` Microsoft Ara dili (MSIL) ve bu Modülün her bir yöntemin JIT derlenmiş sürümleri arasında eşleme bilgilerini korumak JIT Derleyici etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="f663a-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="f663a-107">[in] Bu değer ayarlanırsa `true` hata ayıklama için belirli JIT özgü en iyi duruma getirme ile kodu oluşturmak JIT Derleyici etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="f663a-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f663a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f663a-108">Remarks</span></span>  
 <span data-ttu-id="f663a-109">JIT hata ayıklama hata ayıklayıcısı etkinken yüklenen tüm modülleri için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="f663a-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="f663a-110">Program aracılığıyla etkinleştirme veya ayarlarını devre dışı bırakma genel ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f663a-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f663a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f663a-111">Requirements</span></span>  
 <span data-ttu-id="f663a-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f663a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f663a-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f663a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f663a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f663a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f663a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f663a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
