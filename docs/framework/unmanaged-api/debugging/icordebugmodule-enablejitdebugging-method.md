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
ms.openlocfilehash: 359db27878ea4adf794bcd6221d4b5387026e5c0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710317"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="ae283-102">ICorDebugModule::EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae283-102">ICorDebugModule::EnableJITDebugging Method</span></span>

<span data-ttu-id="ae283-103">Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="ae283-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae283-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ae283-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae283-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae283-105">Parameters</span></span>  

 `bTrackJITInfo`  
 <span data-ttu-id="ae283-106">'ndaki Bu `true` modüldeki, Microsoft ara dili (MSIL) sürümü ve bu modüldeki her YÖNTEMIN JIT derlenmiş sürümü arasındaki eşleme bilgilerini korumak için bu değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae283-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="ae283-107">'ndaki `true` JIT derleyicisinin hata ayıklama için belirli BIR JIT özel iyileştirmelere sahip kod oluşturmasını sağlamak için bu değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae283-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae283-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae283-108">Remarks</span></span>  

 <span data-ttu-id="ae283-109">JıT hata ayıklayıcı, hata ayıklayıcısı etkin olduğunda yüklenen tüm modüller için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="ae283-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="ae283-110">Ayarları programlı bir şekilde etkinleştirmek veya devre dışı bırakmak genel ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ae283-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae283-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae283-111">Requirements</span></span>  

 <span data-ttu-id="ae283-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae283-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae283-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae283-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae283-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae283-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae283-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae283-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
