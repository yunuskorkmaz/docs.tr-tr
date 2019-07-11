---
title: ICorDebugAssembly2::IsFullyTrusted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d231595ab2c7b41d1a24f654e9785b90b34ac780
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744510"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="71279-102">ICorDebugAssembly2::IsFullyTrusted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71279-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="71279-103">Derlemeyi tam güven çalışma zamanı güvenlik sistemi tarafından verilmiş olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="71279-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71279-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71279-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71279-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71279-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="71279-106">[out] `true` çalışma zamanı güvenlik sistemi tarafından; tam güven derleme verilmişse Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="71279-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71279-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71279-107">Remarks</span></span>  
 <span data-ttu-id="71279-108">Bu yöntem, bir HRESULT, derleme için güvenlik ilkesi henüz diğer bir deyişle, hiçbir kod, derleme, çözümlenmedi, CORDBG_E_NOTREADY henüz çalıştırılmamış döndürür.</span><span class="sxs-lookup"><span data-stu-id="71279-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71279-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71279-109">Requirements</span></span>  
 <span data-ttu-id="71279-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71279-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71279-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71279-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71279-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71279-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71279-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71279-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
