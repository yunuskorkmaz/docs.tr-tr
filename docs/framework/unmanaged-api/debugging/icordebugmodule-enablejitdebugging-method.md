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
ms.openlocfilehash: da532ee1b5909a68bedbb9e6f6c96333e88002a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109722"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="e5b2f-102">ICorDebugModule::EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5b2f-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="e5b2f-103">Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b2f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5b2f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5b2f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5b2f-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="e5b2f-106">'ndaki JıT derleyicisinin Microsoft ara dili (MSIL) sürümü ile bu modüldeki her yöntemin JıT derlenmiş sürümü arasındaki eşleme bilgilerini korumasına olanak tanımak için bu değeri `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="e5b2f-107">'ndaki JıT derleyicisinin hata ayıklama için belirli bir JıT özel iyileştirmelere sahip kod oluşturmasını sağlamak için bu değeri `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5b2f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5b2f-108">Remarks</span></span>  
 <span data-ttu-id="e5b2f-109">JıT hata ayıklayıcı, hata ayıklayıcısı etkin olduğunda yüklenen tüm modüller için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="e5b2f-110">Ayarları programlı bir şekilde etkinleştirmek veya devre dışı bırakmak genel ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b2f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5b2f-111">Requirements</span></span>  
 <span data-ttu-id="e5b2f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b2f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5b2f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5b2f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e5b2f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5b2f-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
