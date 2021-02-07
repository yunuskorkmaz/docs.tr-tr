---
description: ': ICorDebugModule:: Enablejıdebugging yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 30077bd586e1cb9cb8766290804e31f5999d9e72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722691"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="807c0-103">ICorDebugModule::EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="807c0-103">ICorDebugModule::EnableJITDebugging Method</span></span>

<span data-ttu-id="807c0-104">Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="807c0-104">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="807c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="807c0-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="807c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="807c0-106">Parameters</span></span>  

 `bTrackJITInfo`  
 <span data-ttu-id="807c0-107">'ndaki Bu `true` modüldeki, Microsoft ara dili (MSIL) sürümü ve bu modüldeki her YÖNTEMIN JIT derlenmiş sürümü arasındaki eşleme bilgilerini korumak için bu değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="807c0-107">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="807c0-108">'ndaki `true` JIT derleyicisinin hata ayıklama için belirli BIR JIT özel iyileştirmelere sahip kod oluşturmasını sağlamak için bu değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="807c0-108">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="807c0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="807c0-109">Remarks</span></span>  

 <span data-ttu-id="807c0-110">JıT hata ayıklayıcı, hata ayıklayıcısı etkin olduğunda yüklenen tüm modüller için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="807c0-110">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="807c0-111">Ayarları programlı bir şekilde etkinleştirmek veya devre dışı bırakmak genel ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="807c0-111">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="807c0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="807c0-112">Requirements</span></span>  

 <span data-ttu-id="807c0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="807c0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="807c0-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="807c0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="807c0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="807c0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="807c0-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="807c0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
