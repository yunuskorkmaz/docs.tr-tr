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
ms.openlocfilehash: 2a8200f942405395429db182b7501a07fc1f930a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212327"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="139c1-102">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="139c1-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="139c1-103">Dinamik bir modül için hata ayıklama simgesi okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="139c1-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="139c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="139c1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="139c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="139c1-105">Parameters</span></span>  
 <span data-ttu-id="139c1-106">riıd</span><span class="sxs-lookup"><span data-stu-id="139c1-106">riid</span></span>  
 <span data-ttu-id="139c1-107">'ndaki Döndürülecek COM arabiriminin IID 'si.</span><span class="sxs-lookup"><span data-stu-id="139c1-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="139c1-108">Genellikle bu bir [ıstreamunmanagedreader arabirimidir](../diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="139c1-108">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="139c1-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="139c1-109">ppObj</span></span>  
 <span data-ttu-id="139c1-110">dışı Döndürülen arabirime yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="139c1-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="139c1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="139c1-111">Return Value</span></span>  
 <span data-ttu-id="139c1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="139c1-112">S_OK</span></span>  
 <span data-ttu-id="139c1-113">Okuyucu başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="139c1-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="139c1-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="139c1-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="139c1-115">Modül, bellek içi veya dinamik bir modül değil.</span><span class="sxs-lookup"><span data-stu-id="139c1-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="139c1-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="139c1-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="139c1-117">Simgeler uygulama tarafından sağlanmadı veya henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="139c1-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="139c1-118">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="139c1-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="139c1-119">Okuyucu oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="139c1-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="139c1-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="139c1-120">Remarks</span></span>  
 <span data-ttu-id="139c1-121">Bu yöntem, bellek içi (dinamik olmayan) modüller için bir sembol okuyucu nesnesi oluşturmak için de kullanılabilir, ancak yalnızca semboller önce kullanılabilir olduktan sonra ( [UpdateModuleSymbols yöntemi](icordebugmanagedcallback-updatemodulesymbols-method.md) geri çağırması tarafından gösterilir).</span><span class="sxs-lookup"><span data-stu-id="139c1-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="139c1-122">Bu yöntem, her çağrılışında yeni bir okuyucu örneği döndürür ( [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)gibi).</span><span class="sxs-lookup"><span data-stu-id="139c1-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="139c1-123">Bu nedenle, hata ayıklayıcı sonucu önbelleğe almalıdır ve yalnızca temeldeki veriler değiştiği zaman yeni bir örnek ister (yani, bir [LoadClass Yöntemi](icordebugmanagedcallback-loadclass-method.md) geri çağırması alındığında).</span><span class="sxs-lookup"><span data-stu-id="139c1-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="139c1-124">Dinamik modüller, ilk tür yükleninceye kadar kullanılabilir simgelere sahip değildir ( [LoadClass Yöntemi](icordebugmanagedcallback-loadclass-method.md) geri çağırması tarafından belirtildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="139c1-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="139c1-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="139c1-125">Requirements</span></span>  
 <span data-ttu-id="139c1-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="139c1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="139c1-127">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="139c1-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="139c1-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="139c1-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="139c1-129">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="139c1-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="139c1-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="139c1-130">See also</span></span>

- [<span data-ttu-id="139c1-131">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="139c1-131">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="139c1-132">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="139c1-132">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="139c1-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="139c1-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
