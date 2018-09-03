---
title: ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 342739f6c71e9c576e557433dc6abd0adbf38c8c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468358"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="deeb7-102">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="deeb7-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="deeb7-103">Dinamik modül için hata ayıklama simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="deeb7-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deeb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="deeb7-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="deeb7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="deeb7-105">Parameters</span></span>  
 <span data-ttu-id="deeb7-106">riid</span><span class="sxs-lookup"><span data-stu-id="deeb7-106">riid</span></span>  
 <span data-ttu-id="deeb7-107">[in] Döndürülecek COM arabirimi Laboratuvardaki.</span><span class="sxs-lookup"><span data-stu-id="deeb7-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="deeb7-108">Bu genellikle bir [Isymunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="deeb7-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="deeb7-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="deeb7-109">ppObj</span></span>  
 <span data-ttu-id="deeb7-110">[out] Döndürülen arabirim işaretçisi için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="deeb7-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="deeb7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="deeb7-111">Return Value</span></span>  
 <span data-ttu-id="deeb7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="deeb7-112">S_OK</span></span>  
 <span data-ttu-id="deeb7-113">Okuyucu başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="deeb7-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="deeb7-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="deeb7-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="deeb7-115">Modül, bellek veya dinamik bir modül değil.</span><span class="sxs-lookup"><span data-stu-id="deeb7-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="deeb7-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="deeb7-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="deeb7-117">Simgeleri uygulama tarafından sağlanan değil veya henüz kullanıma sunulmamıştır.</span><span class="sxs-lookup"><span data-stu-id="deeb7-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="deeb7-118">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="deeb7-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="deeb7-119">Okuyucusu oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="deeb7-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="deeb7-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="deeb7-120">Remarks</span></span>  
 <span data-ttu-id="deeb7-121">Simgeleri ilk kullanılabilir olduktan sonra bu yöntem aynı zamanda bir bellek içi (dinamik olmayan) modüller için Sembol Okuyucu nesnesi oluşturmak için kullanılan, ancak yalnızca olabilir (belirttiği [UpdateModuleSymbols yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) geri çağırma).</span><span class="sxs-lookup"><span data-stu-id="deeb7-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="deeb7-122">Her çağrıldığında bu yöntem, yeni bir okuyucu örneği döndürür. (gibi [CComPtrBase::CoCreateInstance](https://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span><span class="sxs-lookup"><span data-stu-id="deeb7-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](https://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span></span> <span data-ttu-id="deeb7-123">Hata ayıklayıcı bu nedenle, ve sonuç önbellek ister yeni bir örneği temel alınan verileri yalnızca değişmiş olabilir (diğer bir deyişle, bir [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri alındığında).</span><span class="sxs-lookup"><span data-stu-id="deeb7-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="deeb7-124">Dinamik modüller kadar ilk türü yüklenmiş olan simgeleri kullanılabilir gerekmez (gösterildiği gibi [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri çağırma).</span><span class="sxs-lookup"><span data-stu-id="deeb7-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deeb7-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="deeb7-125">Requirements</span></span>  
 <span data-ttu-id="deeb7-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deeb7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deeb7-127">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="deeb7-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deeb7-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="deeb7-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deeb7-129">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="deeb7-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deeb7-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="deeb7-130">See Also</span></span>  
 [<span data-ttu-id="deeb7-131">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="deeb7-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="deeb7-132">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="deeb7-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="deeb7-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="deeb7-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
