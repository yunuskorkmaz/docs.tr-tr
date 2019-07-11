---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ee186604529a3e77a0217c5688df5b62ff8b28c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736985"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="1e34d-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="1e34d-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="1e34d-103">Ortak dil çalışma zamanı (CLR) önceden derlenmiş doğru seçmek için kullandığı bayrağı ayarları geçerli derleyici alır (diğer bir deyişle, yerel) görüntü bu işleme yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="1e34d-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e34d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e34d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e34d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e34d-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="1e34d-106">[out] Bitsel bir birleşimi için bir işaretçi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) yüklenecek önceden derlenmiş doğru görüntüyü seçmek için kullanılan sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="1e34d-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e34d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e34d-107">Remarks</span></span>  
 <span data-ttu-id="1e34d-108">Kullanma [Icordebugprocess2::setdesiredngencompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) CLR yüklemek için önceden derlenmiş doğru görüntüyü seçmek için kullanacağı bayrakları ayarlamanızı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1e34d-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e34d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e34d-109">Requirements</span></span>  
 <span data-ttu-id="1e34d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e34d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e34d-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e34d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e34d-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e34d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e34d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e34d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
