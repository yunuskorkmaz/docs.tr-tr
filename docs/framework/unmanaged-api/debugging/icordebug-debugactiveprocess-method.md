---
title: ICorDebug::DebugActiveProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 1713623fa575bea6df649106b37212f7aeaee6db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723473"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="2a2f1-102">ICorDebug::DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a2f1-102">ICorDebug::DebugActiveProcess Method</span></span>

<span data-ttu-id="2a2f1-103">Hata ayıklayıcıyı mevcut bir işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="2a2f1-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a2f1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2a2f1-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a2f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a2f1-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="2a2f1-106">'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2a2f1-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="2a2f1-107">'ndaki `true` Hata ayıklayıcının, işlem Için Win32 hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları dağıtımı gerekiyorsa olarak ayarlanan Boolean değeri; aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="2a2f1-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="2a2f1-108">dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2a2f1-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a2f1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a2f1-109">Remarks</span></span>  

 <span data-ttu-id="2a2f1-110">, IA-64 tabanlı ve AMD64 tabanlı platformlar gibi Win9x ve x86 olmayan platformlarda birlikte çalışma hata ayıklaması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2a2f1-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a2f1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a2f1-111">Requirements</span></span>  

 <span data-ttu-id="2a2f1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a2f1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a2f1-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a2f1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a2f1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a2f1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a2f1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a2f1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a2f1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a2f1-116">See also</span></span>

- [<span data-ttu-id="2a2f1-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a2f1-117">ICorDebug Interface</span></span>](icordebug-interface.md)
