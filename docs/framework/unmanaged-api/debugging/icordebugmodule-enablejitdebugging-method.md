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
ms.openlocfilehash: 642c4fd600d10ef89a08aa32bef5c8e7455552c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937182"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="afb9c-102">ICorDebugModule::EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb9c-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="afb9c-103">Just-ın-time (JIT) derleyicinin bu modül içindeki yöntemler için hata ayıklama bilgilerini korur olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="afb9c-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afb9c-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afb9c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afb9c-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="afb9c-106">[in] Bu değer kümesine `true` Microsoft Ara dil (MSIL) ve bu modüldeki her yöntemi JIT olarak derlenmiş sürümleri arasında eşleme bilgilerini korumak JIT derleyicisi etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="afb9c-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="afb9c-107">[in] Bu değer kümesine `true` JIT Derleyici kodu ile hata ayıklama için belirli özel JIT iyileştirmelerini etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="afb9c-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afb9c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afb9c-108">Remarks</span></span>  
 <span data-ttu-id="afb9c-109">JIT hata ayıklama, hata ayıklayıcısı etkinken, yüklenen tüm modüller için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="afb9c-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="afb9c-110">Program aracılığıyla etkinleştirme veya ayarları devre dışı bırakma genel ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="afb9c-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb9c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afb9c-111">Requirements</span></span>  
 <span data-ttu-id="afb9c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb9c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb9c-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afb9c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afb9c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afb9c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afb9c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb9c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
