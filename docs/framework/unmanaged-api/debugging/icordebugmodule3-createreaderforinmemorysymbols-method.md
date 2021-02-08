---
description: ': ICorDebugModule3:: CreateReaderForInMemorySymbols yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: af037cc891e83f53fd94bad290f40286ed665e6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790782"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="23dc4-103">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23dc4-103">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>

<span data-ttu-id="23dc4-104">Dinamik bir modül için hata ayıklama simgesi okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23dc4-104">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23dc4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23dc4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="23dc4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23dc4-106">Parameters</span></span>  

 <span data-ttu-id="23dc4-107">riıd</span><span class="sxs-lookup"><span data-stu-id="23dc4-107">riid</span></span>  
 <span data-ttu-id="23dc4-108">'ndaki Döndürülecek COM arabiriminin IID 'si.</span><span class="sxs-lookup"><span data-stu-id="23dc4-108">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="23dc4-109">Genellikle bu bir [ıstreamunmanagedreader arabirimidir](../diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23dc4-109">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="23dc4-110">ppObj</span><span class="sxs-lookup"><span data-stu-id="23dc4-110">ppObj</span></span>  
 <span data-ttu-id="23dc4-111">dışı Döndürülen arabirime yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="23dc4-111">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23dc4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23dc4-112">Return Value</span></span>  

 <span data-ttu-id="23dc4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="23dc4-113">S_OK</span></span>  
 <span data-ttu-id="23dc4-114">Okuyucu başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="23dc4-114">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="23dc4-115">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="23dc4-115">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="23dc4-116">Modül, bellek içi veya dinamik bir modül değil.</span><span class="sxs-lookup"><span data-stu-id="23dc4-116">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="23dc4-117">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23dc4-117">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="23dc4-118">Simgeler uygulama tarafından sağlanmadı veya henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="23dc4-118">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="23dc4-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="23dc4-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="23dc4-120">Okuyucu oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="23dc4-120">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23dc4-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23dc4-121">Remarks</span></span>  

 <span data-ttu-id="23dc4-122">Bu yöntem, bellek içi (dinamik olmayan) modüller için bir sembol okuyucu nesnesi oluşturmak için de kullanılabilir, ancak yalnızca semboller önce kullanılabilir olduktan sonra ( [UpdateModuleSymbols yöntemi](icordebugmanagedcallback-updatemodulesymbols-method.md) geri çağırması tarafından gösterilir).</span><span class="sxs-lookup"><span data-stu-id="23dc4-122">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="23dc4-123">Bu yöntem, her çağrılışında yeni bir okuyucu örneği döndürür ( [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)gibi).</span><span class="sxs-lookup"><span data-stu-id="23dc4-123">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="23dc4-124">Bu nedenle, hata ayıklayıcı sonucu önbelleğe almalıdır ve yalnızca temeldeki veriler değiştiği zaman yeni bir örnek ister (yani, bir [LoadClass Yöntemi](icordebugmanagedcallback-loadclass-method.md) geri çağırması alındığında).</span><span class="sxs-lookup"><span data-stu-id="23dc4-124">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="23dc4-125">Dinamik modüller, ilk tür yükleninceye kadar kullanılabilir simgelere sahip değildir ( [LoadClass Yöntemi](icordebugmanagedcallback-loadclass-method.md) geri çağırması tarafından belirtildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="23dc4-125">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23dc4-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23dc4-126">Requirements</span></span>  

 <span data-ttu-id="23dc4-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23dc4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23dc4-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="23dc4-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23dc4-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="23dc4-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23dc4-130">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="23dc4-130">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23dc4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23dc4-131">See also</span></span>

- [<span data-ttu-id="23dc4-132">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23dc4-132">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="23dc4-133">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23dc4-133">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="23dc4-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="23dc4-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
