---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugModule2:: SetJITCompilerFlags yöntemi'
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
ms.openlocfilehash: 72139c2fefc0eab7e76e38d07558e4386b47bc34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801078"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="381ee-103">ICorDebugModule2::SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="381ee-103">ICorDebugModule2::SetJITCompilerFlags Method</span></span>

<span data-ttu-id="381ee-104">Bu ICorDebugModule2 'ın tam zamanında (JıT) derlemesini denetleyen bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="381ee-104">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="381ee-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="381ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="381ee-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="381ee-107">'ndaki [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="381ee-107">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="381ee-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="381ee-108">Remarks</span></span>  

 <span data-ttu-id="381ee-109">`dwFlags`Değer geçersizse, `SetJITCompilerFlags` Yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="381ee-109">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="381ee-110">`SetJITCompilerFlags`Yöntemi yalnızca bu modül Için [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) geri çağırması içinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="381ee-110">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="381ee-111">Geri çağırma işlemi geri alındıktan sonra çağrı denemeleri `ICorDebugManagedCallback::LoadModule` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="381ee-111">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="381ee-112">Düzenle ve devam et, 64-bit veya Win9x platformlarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="381ee-112">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="381ee-113">Bu nedenle, `SetJITCompilerFlags` yöntemi ' de ayarlanmış CORDEBUG_JIT_ENABLE_ENC bayrağı ile bu iki platformundan birine çağırırsanız `dwFlags` , `SetJITCompilerFlags` [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md)gibi, düzenleme ve devam etme yöntemine özgü Yöntem ve tüm yöntemler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="381ee-113">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="381ee-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="381ee-114">Requirements</span></span>  

 <span data-ttu-id="381ee-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="381ee-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="381ee-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="381ee-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="381ee-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="381ee-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="381ee-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="381ee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
