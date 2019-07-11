---
title: ICorDebugModule2::SetJITCompilerFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 114f4ff261d9612a81d17bf5b3df2f87323f77f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764195"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="d83ec-102">ICorDebugModule2::SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d83ec-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="d83ec-103">Bu Icordebugmodule2 just-in-time (JIT) derlenmesi denetleyen bayraklar ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d83ec-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d83ec-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d83ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d83ec-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d83ec-106">[in] Bitsel bir birleşimi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="d83ec-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d83ec-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d83ec-107">Remarks</span></span>  
 <span data-ttu-id="d83ec-108">Varsa `dwFlags` değeri geçersiz `SetJITCompilerFlags` yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d83ec-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="d83ec-109">`SetJITCompilerFlags` Yöntemi yalnızca içinde çağrılabilir [Icordebugmanagedcallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) bu modül için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="d83ec-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="d83ec-110">Bundan sonra çağırma girişiminde `ICorDebugManagedCallback::LoadModule` geri çağırma, teslim başarısız.</span><span class="sxs-lookup"><span data-stu-id="d83ec-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="d83ec-111">Düzenle ve devam et desteklenmez 64-bit veya Win9x platformlar.</span><span class="sxs-lookup"><span data-stu-id="d83ec-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="d83ec-112">Bu nedenle, eğer `SetJITCompilerFlags` yöntemi bu iki platform kümesinde CORDEBUG_JIT_ENABLE_ENC bayrağıyla birini `dwFlags`, `SetJITCompilerFlags` yöntemi ve belirli tüm yöntemler, Düzenle ve devam et, gibi [Icordebugmodule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d83ec-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d83ec-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d83ec-113">Requirements</span></span>  
 <span data-ttu-id="d83ec-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83ec-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83ec-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d83ec-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d83ec-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d83ec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d83ec-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83ec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
