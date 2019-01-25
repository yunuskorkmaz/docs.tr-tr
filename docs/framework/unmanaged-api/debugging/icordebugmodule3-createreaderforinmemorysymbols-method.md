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
ms.openlocfilehash: 931a0cbd8dd15a62780a7bcf03d3d354f552232c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628350"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="5644e-102">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5644e-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="5644e-103">Dinamik modül için hata ayıklama simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5644e-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5644e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5644e-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5644e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5644e-105">Parameters</span></span>  
 <span data-ttu-id="5644e-106">riid</span><span class="sxs-lookup"><span data-stu-id="5644e-106">riid</span></span>  
 <span data-ttu-id="5644e-107">[in] Döndürülecek COM arabirimi Laboratuvardaki.</span><span class="sxs-lookup"><span data-stu-id="5644e-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="5644e-108">Bu genellikle bir [Isymunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5644e-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="5644e-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="5644e-109">ppObj</span></span>  
 <span data-ttu-id="5644e-110">[out] Döndürülen arabirim işaretçisi için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5644e-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5644e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5644e-111">Return Value</span></span>  
 <span data-ttu-id="5644e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5644e-112">S_OK</span></span>  
 <span data-ttu-id="5644e-113">Okuyucu başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="5644e-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="5644e-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="5644e-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="5644e-115">Modül, bellek veya dinamik bir modül değil.</span><span class="sxs-lookup"><span data-stu-id="5644e-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="5644e-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5644e-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="5644e-117">Simgeleri uygulama tarafından sağlanan değil veya henüz kullanıma sunulmamıştır.</span><span class="sxs-lookup"><span data-stu-id="5644e-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="5644e-118">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="5644e-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5644e-119">Okuyucusu oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="5644e-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5644e-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5644e-120">Remarks</span></span>  
 <span data-ttu-id="5644e-121">Simgeleri ilk kullanılabilir olduktan sonra bu yöntem aynı zamanda bir bellek içi (dinamik olmayan) modüller için Sembol Okuyucu nesnesi oluşturmak için kullanılan, ancak yalnızca olabilir (belirttiği [UpdateModuleSymbols yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) geri çağırma).</span><span class="sxs-lookup"><span data-stu-id="5644e-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="5644e-122">Her çağrıldığında bu yöntem, yeni bir okuyucu örneği döndürür. (gibi [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="5644e-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="5644e-123">Hata ayıklayıcı bu nedenle, ve sonuç önbellek ister yeni bir örneği temel alınan verileri yalnızca değişmiş olabilir (diğer bir deyişle, bir [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri alındığında).</span><span class="sxs-lookup"><span data-stu-id="5644e-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="5644e-124">Dinamik modüller kadar ilk türü yüklenmiş olan simgeleri kullanılabilir gerekmez (gösterildiği gibi [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri çağırma).</span><span class="sxs-lookup"><span data-stu-id="5644e-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5644e-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5644e-125">Requirements</span></span>  
 <span data-ttu-id="5644e-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5644e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5644e-127">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5644e-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5644e-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5644e-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5644e-129">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="5644e-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5644e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5644e-130">See also</span></span>
- [<span data-ttu-id="5644e-131">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5644e-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="5644e-132">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5644e-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="5644e-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5644e-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
