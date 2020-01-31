---
title: ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 2b64122489481c6b0fde605015720d0a56ba8fe2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788319"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="9f379-102">ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f379-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="9f379-103">Hata ayıklayıcısını, ortak dil çalışma zamanı modülü simgelerinin değiştiği hakkında bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="9f379-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f379-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f379-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f379-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f379-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9f379-106">'ndaki Simgenin değiştiği modülün bulunduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f379-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="9f379-107">'ndaki Simgelerin değiştiği modülü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f379-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="9f379-108">'ndaki Değiştirilen sembolleri içeren Win32 COM `IStream` nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f379-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f379-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f379-109">Remarks</span></span>  
 <span data-ttu-id="9f379-110">Bu yöntem, [ıvmunmanagedreader:: UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) veya [ıımunmanagedreader:: Synccesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)çağırarak hata ayıklayıcının bir modülün sembol görünümünü güncelleştirme fırsatı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f379-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="9f379-111">Bu geri çağırma aynı modül için birden çok kez gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="9f379-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="9f379-112">Bir hata ayıklayıcı, ilişkisiz kaynak düzeyinde kesme noktaları bağlamayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="9f379-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f379-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f379-113">Requirements</span></span>  
 <span data-ttu-id="9f379-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f379-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f379-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9f379-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f379-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9f379-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f379-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f379-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f379-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f379-118">See also</span></span>

- [<span data-ttu-id="9f379-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f379-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
