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
ms.openlocfilehash: 2358cee1b3a9aa50fb1f0e61d558f164a39aa86c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137357"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="ab257-102">ICorDebugModule2::SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab257-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="ab257-103">Bu ICorDebugModule2 'ın tam zamanında (JıT) derlemesini denetleyen bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab257-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab257-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab257-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab257-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab257-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="ab257-106">'ndaki [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="ab257-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab257-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab257-107">Remarks</span></span>  
 <span data-ttu-id="ab257-108">`dwFlags` değeri geçersizse, `SetJITCompilerFlags` yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ab257-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="ab257-109">`SetJITCompilerFlags` yöntemi yalnızca bu modül için [ICorDebugManagedCallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) geri çağırması içinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab257-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="ab257-110">`ICorDebugManagedCallback::LoadModule` geri çağırma işlemi teslim edildikten sonra bu aramayı çağırma girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ab257-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="ab257-111">Düzenle ve devam et, 64-bit veya Win9x platformlarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ab257-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="ab257-112">Bu nedenle, bu iki platformda `SetJITCompilerFlags` yöntemini `dwFlags`CORDEBUG_JIT_ENABLE_ENC bayrağı ayarlanmış olarak çağırırsanız, `SetJITCompilerFlags` yöntemi ve [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)gibi Düzenle ve devam et 'e özgü tüm yöntemler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ab257-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab257-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab257-113">Requirements</span></span>  
 <span data-ttu-id="ab257-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab257-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab257-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab257-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab257-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ab257-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab257-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab257-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
