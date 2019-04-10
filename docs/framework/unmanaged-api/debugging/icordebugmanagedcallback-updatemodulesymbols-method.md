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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581ea4f974bfec3961a32cd7c9985a5e45d2bddd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209989"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="94077-102">ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94077-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="94077-103">Hata ayıklayıcı ortak dil çalışma zamanı modülü için Sembol değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="94077-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94077-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94077-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94077-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94077-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="94077-106">[in] Hangi simgelerin değişmiş modülü içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="94077-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="94077-107">[in] Modül, semboller değiştirildi temsil eden bir Icordebugmodule nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="94077-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="94077-108">[in] Bir Win32 COM işaretçisi `IStream` değiştirilmiş simgeleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="94077-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94077-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94077-109">Remarks</span></span>  
 <span data-ttu-id="94077-110">Bu yöntem, hata ayıklayıcı'nın bir modülün sembolleri görünümünü çağırarak güncelleştirmek için bir fırsat sağlar. [Isymunmanagedreader::updatesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) veya [Isymunmanagedreader::replacesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="94077-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="94077-111">Bu geri çağırma aynı modülü için birden çok kez gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="94077-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="94077-112">Bir hata ayıklayıcı ilişkisiz kaynak düzeyinde kesme noktaları bağlama çalışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="94077-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94077-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94077-113">Requirements</span></span>  
 <span data-ttu-id="94077-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94077-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94077-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94077-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94077-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94077-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="94077-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="94077-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94077-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94077-118">See also</span></span>

- [<span data-ttu-id="94077-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94077-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
