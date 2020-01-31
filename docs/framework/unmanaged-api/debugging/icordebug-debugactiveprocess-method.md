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
ms.openlocfilehash: 2d71cebb77ed3ca586e857710667c0077f4f76ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793579"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="b757f-102">ICorDebug::DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b757f-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="b757f-103">Hata ayıklayıcıyı mevcut bir işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="b757f-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b757f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b757f-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b757f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b757f-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b757f-106">'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b757f-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="b757f-107">'ndaki Hata ayıklayıcı işlem için Win32 hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları dağıtmak için `true` olarak ayarlanan Boole değeri; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b757f-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b757f-108">dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b757f-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b757f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b757f-109">Remarks</span></span>  
 <span data-ttu-id="b757f-110">, IA-64 tabanlı ve AMD64 tabanlı platformlar gibi Win9x ve x86 olmayan platformlarda birlikte çalışma hata ayıklaması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b757f-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b757f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b757f-111">Requirements</span></span>  
 <span data-ttu-id="b757f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b757f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b757f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b757f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b757f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b757f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b757f-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b757f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b757f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b757f-116">See also</span></span>

- [<span data-ttu-id="b757f-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b757f-117">ICorDebug Interface</span></span>](icordebug-interface.md)
